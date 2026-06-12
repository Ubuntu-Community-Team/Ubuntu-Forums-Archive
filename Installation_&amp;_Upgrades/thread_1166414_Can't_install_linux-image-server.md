---
title: "Can't install linux-image-server"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by modmadmike on 2009-05-21
In 9.04 on x86_64
```
$ sudo apt-get install linux-image-serverReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java icedtea-6-jre-cacao openjdk-6-jre-lib libdvbpsi4
  openjdk-6-jre-headless libvlc2 libsdl-image1.2 ttf-telugu-fonts vlc-nox
  ttf-bengali-fonts libmatroska0 tzdata-java cabextract rhino liblua5.1-0
  ca-certificates-java vlc-data ttf-kannada-fonts ttf-wqy-zenhei libtar
  libvlccore0 libebml0 ttf-oriya-fonts
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.28-11-server
Suggested packages:
  fdutils linux-doc-2.6.28 linux-source-2.6.28
The following NEW packages will be installed:
  linux-image-2.6.28-11-server linux-image-server
0 upgraded, 2 newly installed, 0 to remove and 62 not upgraded.
Need to get 0B/24.3MB of archives.
After this operation, 112MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package linux-image-2.6.28-11-server.
(Reading database ... 161736 files and directories currently installed.)
Unpacking linux-image-2.6.28-11-server (from .../linux-image-2.6.28-11-server_2.6.28-11.42_amd64.deb) ...
Done.
Selecting previously deselected package linux-image-server.
Unpacking linux-image-server (from .../linux-image-server_2.6.28.11.15_amd64.deb) ...
Setting up linux-image-2.6.28-11-server (2.6.28-11.42) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.28-11-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.28-11-server; however:
  Package linux-image-2.6.28-11-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-image-2.6.28-11-server
 linux-image-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by stroyan on 2009-05-21
You might be seeing the same problem reported as
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330834](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330834)

---

### Post by modmadmike on 2009-08-13
> **stroyan said:**
> You might be seeing the same problem reported as
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330834](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330834)

Oh well im running Karmic now and I don't have this problem lol Also I can now use the RT kernel which didn't work in 9.04 for me.

---

