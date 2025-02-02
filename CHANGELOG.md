# Changelog

## v0.0.18 (unreleased)

## v0.0.17

- Fix locale warnings on MacOS
- Make `executables` a list, and optional, in `mkHaskellPackage`
- Add `addCabalExecutable` to Haskell projects
- Make `garn init` on Haskell projects fill in the `executables` based on the cabal file.
- For git repositories, add untracked files to build sandboxes for `Check`s and
  `Package`s.
- Tweak the API for creating `Environment`s, making it easier to create
  `Environment`s that have a source directory
- Fix needing to use `--` twice in `garn run` in order to pass arguments to
  executables.
- Allow entering top-level `Environment`s with `garn enter`.
- `Environment.mkNpmProject` and `Environment.mkYarnProject` don't expose a
  `devShell` field anymore, since that was a duplicate of `defaultEnvironment`.

- Create a new `edit` command. This opens VSCodium with deno LSP already set up,
  in exactly the same way as the old `editGarnConfig` function did. (That
  function has now been removed.)

## v0.0.16

- Allow to build packages that are nested within projects with `garn build projectName.packageName`.
- Allow to build top-level packages with `garn build packageName`.
- Allow adding packages to projects with `.addPackage("packageName", "{build script writing to $out}")`.
- Add `Project.add`, a function to apply so-called `Plugin`s to a project. This
  provides a nice way to bundle up more complex project modifications into a
  single declaration. It also allows to use `Plugin`s from other sources,
  including third-party libraries.
- Expose some useful nested nix packages in the garn `nixpkgs.ts` package.
- Add `garn.javascript.vite`, a `Plugin` that adds fields for bundling vite projects into a `Package`.
- Add `garn.deployToGhPages` plugin to help publish `Packages` to github pages.

## v0.0.15

- Added a `--version` flag
- Added simpler overloads for `Project.addCheck`, `Project.addExecutable`,
  `Project.check`, `Project.shell`, etc.. So you don't have to use the unusual
  backtick syntax.
- Added `golang` version `1.21`.
- `garn run` handles non-zero exitcodes better:
  - Exit codes of child-processes are forwarded by `garn`.
  - `garn` doesn't output a confusing error message about a failed child-process.
- Don't include unused flake inputs in the generated flake files.
