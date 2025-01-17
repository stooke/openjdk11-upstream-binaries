# OpenJDK Upstream Binaries (JDK 11u)

Not to be confused with the official AdoptOpenJDK binaries [openjdk11-binaries](https://github.com/AdoptOpenJDK/openjdk11-binaries).

_openjdk11-upstream-binaries_ are pure unaltered builds from the OpenJDK mercurial jdk11u code stream which have been built by Red Hat on behalf of the OpenJDK community jdk11u updates project.

## Build Scripts

This repository also contains [build scripts](install-rhel6-deps-build-openjdk11.sh) which were used to produce binaries released under this repository. See [usage](README.md#Usage) for more information.

### Usage

These build scripts require a compiler which supports the C++11 standard for the in-tree harfbuzz library. In order to get access to such a compiler on older systems it is recommended to subscribe the build host to the Red Hat Software Collections channel using subscription-manager. More details on how to do that here:
https://access.redhat.com/documentation/en-us/red_hat_software_collections/1/html/1.2_release_notes/chap-installation

On your newly commissioned RHEL machine, you can run these steps to produce a build:

    $ wget -O openjdk11-upstream-binaries-master.tar.gz "https://github.com/AdoptOpenJDK/openjdk11-upstream-binaries/archive/master.tar.gz"
    $ tar -xf openjdk11-upstream-binaries-master.tar.gz
    $ cd openjdk11-upstream-binaries-master
    $ bash install-rhel-deps-build-openjdk11.sh

This will produce a file in `/home/openjdk` called `openjdk-*-all-artefacts.tar.gz`,
which is about 742 MB in size, containing:

 * The JDK 11 build log
 * The JDK 11 image without debuginfo
 * The JKD 11 debuginfo files for the JDK 11 image (overlay)
 * The JDK 11 image in slowdebug version
 * The JDK 11 debuginfo files for the slowdebug version (overlay)
 * The JDK 11 source tarball

Example:

    jdk11u/build/release/images/OpenJDK11U-x64_linux_11.0.3_4_ea-debuginfo.tar.gz
    jdk11u/build/release/images/OpenJDK11U-x64_linux_11.0.3_4_ea.tar.gz
    jdk11u/build/OpenJDK11U-sources_11.0.3_4_ea.tar.gz
    jdk11u/build/slowdebug/images/OpenJDK11U-x64_linux_11.0.3_4_ea-slowdebug.tar.gz
    jdk11u/build/slowdebug/images/OpenJDK11U-x64_linux_11.0.3_4_ea-slowdebug-debuginfo.tar.gz
    jdk11u/overall-build.log

### Only Build OpenJDK 11 (without Build Requirements)

If you already have the build requirements for building OpenJDK 11 installed, you can
use a simpler build script to build OpenJDK 11:

    $ wget -O openjdk11-upstream-binaries-master.tar.gz "https://github.com/AdoptOpenJDK/openjdk11-upstream-binaries/archive/master.tar.gz"
    $ tar -xf openjdk11-upstream-binaries-master.tar.gz
    $ cd openjdk11-upstream-binaries-master
    $ bash build-openjdk11.sh
