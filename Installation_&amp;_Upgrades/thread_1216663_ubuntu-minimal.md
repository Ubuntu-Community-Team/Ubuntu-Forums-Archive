---
title: "ubuntu-minimal"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by cccc on 2009-07-18
hi

What's **ubuntu-minimal**?
Should be installed on a default Ubuntu Karmic installation?

---

### Post by jerome1232 on 2009-07-18
```
apt-cache show ubuntu-minimal 
Package: ubuntu-minimal
Priority: important
Section: metapackages
Installed-Size: 56
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Architecture: amd64
Source: ubuntu-meta
Version: 1.140
Depends: adduser, apt, apt-utils, bzip2, console-setup, debconf, dhcp3-client, eject, gnupg, ifupdown, initramfs-tools, iproute, iputils-ping, kbd, less, locales, lsb-release, makedev, mawk, module-init-tools, net-tools, netbase, netcat, ntpdate, passwd, procps, python, startup-tasks, sudo, sysklogd, system-services, tasksel, tzdata, ubuntu-keyring, udev, upstart, upstart-compat-sysv, upstart-logd, vim-tiny, whiptail
Filename: pool/main/u/ubuntu-meta/ubuntu-minimal_1.140_amd64.deb
Size: 28000
MD5sum: 4115cdce5d5f2cfa15641203471465ce
SHA1: 3c98aa28c4478bbb8c8e94ccf070d0e36c8f5298
SHA256: 8c2b1a21c998f1696860cc44b3e6aa089d70737394edd09848fa19f6128034f2
[B]Description: Minimal core of Ubuntu
 This package depends on all of the packages in the Ubuntu minimal system,
 that is a functional command-line system with the following capabilities:
 .
  - Boot
  - Detect hardware
  - Connect to a network
  - Install packages
  - Perform basic diagnostics
 .
 It is also used to help ensure proper upgrades, so it is recommended that
 it not be removed.[/B]
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: minimal

```

---

