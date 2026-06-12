---
title: "Error upgrading 8.04 to 8.10"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by ww9rivers on 2009-06-05
I got an "Error during upgrade" message with the following details:
```
W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.bz2  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```Any idea where to look for problems?

Here is my sources list after trying to upgrade using the "Update Manager":

```
$ grep -v ^# /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```Thanks!

---

### Post by zvacet on 2009-06-05
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ww9rivers on 2009-06-05
Thanks! But that doesn't seem to do much.

```
# sudo apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg
Hit http://oss.oracle.com unstable Release.gpg
Hit http://debian.opennms.org unstable Release.gpg
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://oss.oracle.com unstable/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://oss.oracle.com unstable/non-free Translation-en_US
Ign http://debian.opennms.org unstable/main Translation-en_US
Hit http://debian.opennms.org unstable Release
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://debian.opennms.org unstable/main Packages
Hit http://debian.opennms.org unstable/main Sources
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Hit http://oss.oracle.com unstable Release
Hit http://oss.oracle.com unstable/main Packages
Hit http://oss.oracle.com unstable/non-free Packages
Ign http://pkg-nav.alioth.debian.org etch Release.gpg
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://pkg-nav.alioth.debian.org etch/local Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://pkg-nav.alioth.debian.org etch Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Ign http://pkg-nav.alioth.debian.org etch/local Packages
Hit http://pkg-nav.alioth.debian.org etch/local Packages
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done

# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

