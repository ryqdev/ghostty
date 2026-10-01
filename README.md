# Ghostty

This repository is a fork of [ghostty-org/ghostty](https://github.com/ghostty-org/ghostty).

## Build and run locally (macOS)

Prerequisites:

- Zig **0.16.0**, as specified in `build.zig.zon`.
- Xcode **26 or newer**, with the macOS SDK and Metal Toolchain installed.
- Homebrew, to install gettext and Nushell:

  ```sh
  brew install gettext nushell
  ```

Ensure the active developer directory points to Xcode:

```sh
sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
```

From the repository root, build and launch an optimized local version:

```sh
zig build -Doptimize=ReleaseFast -Demit-macos-app=false &&
  nu macos/build.nu --configuration ReleaseLocal &&
  open macos/build/ReleaseLocal/Ghostty.app
```

This builds the Zig library and resources, builds the macOS app, and launches it.
The app is located at `macos/build/ReleaseLocal/Ghostty.app`. The first build
requires internet access to download dependencies and may take several minutes.
