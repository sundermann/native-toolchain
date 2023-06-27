# buildroot-nc4-ports

Ports for [Unofficial webOS NDK](https://github.com/openlgtv/buildroot-nc4) supporting systems other than Linux x86_64

---

## Supported Host Platforms

* [Linux x86_64 (original)](https://github.com/openlgtv/buildroot-nc4/releases/latest)
* macOS x86_64

## Install

1. Download tarball for your system from [latest release](https://github.com/mariotaku/buildroot-nc4-sdk-ports/releases)
2. Extract the tarball to the location you want (please avoid having spaces and special characters in the path)
3. Run `relocate-sdk.sh` in extracted contents

## Usage

### CMake

When you build a CMake project in command line, assign `CMAKE_TOOLCHAIN_FILE` with toolchain file. 

```shell
cmake -B build -DCMAKE_TOOLCHAIN_FILE=/path/to/extracted/tarball/arm-webos-linux-gnueabi_sdk-buildroot/share/buildroot/toolchainfile.cmake
```

For VSCode [CMake Tools](https://github.com/microsoft/vscode-cmake-tools/), add entry in 
[Kit options](https://github.com/microsoft/vscode-cmake-tools/blob/main/docs/kits.md#kit-options):

```json
[
    {
        "name": "webOS",
        "toolchainFile": "/path/to/extracted/tarball/arm-webos-linux-gnueabi_sdk-buildroot/share/buildroot/toolchainfile.cmake"
    }
]
```

### Build

If your machine is not included, you can build it on your local machine.

#### Prerequisites

* GCC
* CMake

#### Build Toolchain Port

Please set `CC` and `CXX` environment variable to binary of GCC you have installed.
If your `LANG` environment variable is not `en_US.UTF-8`, please set to that.

```shell
cmake -E make_directory build
cmake -B build -DCMAKE_INSTALL_PREFIX=/path/to/install/location
cmake --build build 
cmake --install build # Ensure you have write permission to the prefix you set
```

Then the toolchain will be installed to the location you want automatically.