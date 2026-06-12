---
title: "No sound (completely new to linux)"
date: 2008-09-17
forum: Hardware
---

### Post by jman272004 on 2008-09-17
As I stated I am completely new to linux, I know so little it about it but I am willing to learn, and I am slowly learning.

I have an alienware area51 m15x laptop dual booting with vista:(.

I have sound in windows vista, yet none in Ubuntu.  I have searched the web for help and read some posts but nothing has helped yet.

I have checked alsamixer as many people have suggested in other threads and all is unmuted and maxed.  My volume is maxed and unmuted.

I read [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) and nothing helped, and my head is pounding with all the information that I have bombarded myself with in so little of a time frame.

I have txt files attacted with output from "uname -a" and "lspci -v" named as the command.


From "dpkg -s linux-ubuntu-modules-$(uname -r)"
```
Package: linux-ubuntu-modules-2.6.24-19-generic
Status: install ok installed
Priority: optional
Section: base
Installed-Size: 15280
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-ubuntu-modules-2.6.24
Version: 2.6.24-19.28
Provides: ndiswrapper-modules-1.9
Depends: linux-image-2.6.24-19-generic
Pre-Depends: dpkg (>= 1.10.24)
Description: Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64
 This package contains modules supplied by Ubuntu for Linux kernel 2.6.24 on
 x86/x86_64.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.

```

Then the alsa link...[http://www.alsa-project.org/db/?f=46c6589ee87e61c47eb85094a2a7d03e69b540e2](http://www.alsa-project.org/db/?f=46c6589ee87e61c47eb85094a2a7d03e69b540e2)



Thank you for your time.

---

