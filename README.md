<div align="center">

<img src=".github/assets/openstream-icon.png" alt="OpenStream icon" width="96">

# OpenStream for Android

**A media player for the movies, shows and live TV you already have, on Android phones, tablets, Google TV and XR headsets.**

[![CI](https://img.shields.io/github/actions/workflow/status/orgista/openstream-android/ci.yml?branch=main&style=flat-square&label=CI)](https://github.com/orgista/openstream-android/actions/workflows/ci.yml)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/orgista/openstream-android/badge)](https://scorecard.dev/viewer/?uri=github.com/orgista/openstream-android)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache%202.0-2ea44f?style=flat-square)](LICENSE)
[![Platforms](https://img.shields.io/badge/platforms-Android%20%C2%B7%20Google%20TV%20%C2%B7%20XR-1c1e20?style=flat-square&logo=android&logoColor=white)](#apps)

[orgista.com/openstream](https://orgista.com/openstream) · [Build from source](#build-from-source) · [Security](SECURITY.md) · [Apple apps](https://github.com/orgista/openstream-apple)

</div>

---

OpenStream plays media you own: your Jellyfin, Emby or Plex server, network shares (SMB), files on your device, and the
live TV playlist and guide your TV provider gives you. OpenStream does not provide, host or recommend any content; it
starts empty and plays only what you connect.

## Apps

| Folder | App | Notes |
| --- | --- | --- |
| `native/android-xr` | Phones, tablets, Googlebook and Android XR | Jetpack Compose; the shared Kotlin sources |
| `native/google-tv` | Google TV | Leanback build that compiles the shared sources from `native/android-xr` |
| `native/android-xr-scene` | Android XR SceneCore | Immersive playback |
| `native/meta-quest` | Meta Quest | OpenXR video layers |
| `native/openxr` | Shared C++ | Projection and session code used by the XR apps |

## Build from source

You need JDK 17, the Android SDK (NDK 29 and CMake 4.1 for the XR builds) and Gradle 9.5.

```bash
git clone https://github.com/orgista/openstream-android.git && cd openstream-android
gradle -p native/android-xr testDebugUnitTest assembleDebug     # phone, tablet, XR
gradle -p native/google-tv testDebugUnitTest assembleDebug      # Google TV
sh scripts/openxr-core-test.sh && sh scripts/quest-layer-test.sh # C++ cores
```

Debug builds are signed with the debug key and are for development only.

## Releases

- **Versions** follow [Semantic Versioning](https://semver.org/). A version with a suffix (`v1.4.0-beta.1`) is a pre-release.
- **Cadence:** a release when a change is ready, and at least one maintenance release a month while the project is in active development. Security fixes ship within 7 days of a confirmed report.
- **Every release** gets a `SHA256SUMS` file and a GitHub build attestation.
- **Support:** only the latest release gets fixes.

This repository is a public copy of the source, updated with each release. Full policy:
[orgista release process](https://github.com/orgista/.github/blob/main/RELEASING.md).

## Contributing

Issues and pull requests are welcome. See [CONTRIBUTING](https://github.com/orgista/.github/blob/main/CONTRIBUTING.md)
and the [Code of Conduct](https://github.com/orgista/.github/blob/main/CODE_OF_CONDUCT.md). Changes should pass CI.

## License

Apache-2.0. See [LICENSE](LICENSE). The OpenStream name and icon are not covered by the license.
