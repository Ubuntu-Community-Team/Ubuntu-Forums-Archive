---
title: "ATI drivers"
date: 2009-07-03
forum: Hardware
---

### Post by neonetos on 2009-07-03
I wanted to install graphic drivers for my radeon x1650pro so I referred to:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

First I did the manual install, using the drivers from the ATI website. Rebooted, didn't work. So I set drivers back to default and attempted to do the "easier" way but when I enter the command
```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
```It gets kicked back saying
```
Package `linux-restricted-modules-uname' is not installed and no info is available.
Package `-r' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-restricted-modules-uname -r is not installed
```Is there something I'm doing wrong? or should've done prior to entering that. If anyone can shed some light on this it'd be appreciated.

---

