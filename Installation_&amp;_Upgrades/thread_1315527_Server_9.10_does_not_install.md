---
title: "Server 9.10 does not install"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by aajax on 2009-11-05
When trying to install Ubuntu Server 9.10 it fails with an indication that it cannot complete the kernel installation.  On the same machine Ubuntu Server 8.04 installs properly.

The subject computer is a bit aged (Pentium 3 SMP, that uses SCSI drives).

The Ubuntu Website doesn't make it easy to download releases prior to 9.10.  Hopefully, there is a way to get the past distributions.  If so would someone please enlighten me?

---

### Post by Mighty_Joe on 2009-11-05
Did you accidentally download the 64-bit Server version?  It is the default, but it is not supported by your CPU.  The iso will be named something like "ubuntu-9.10-server-amd64.iso".  You want [ubuntu-9.10-server-i386.iso]("http://releases.ubuntu.com/karmic/ubuntu-9.10-server-i386.iso")
All the currently supported releases of Ubuntu are [here]("http://releases.ubuntu.com/")

---

