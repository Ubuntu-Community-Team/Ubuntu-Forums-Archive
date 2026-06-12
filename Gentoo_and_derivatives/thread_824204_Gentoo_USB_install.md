---
title: "Gentoo USB install"
date: 2008-06-09
forum: Gentoo and derivatives
---

### Post by Raccoon1400 on 2008-06-09
Using the instructions from pendrivelinux.com, my flash drive will now boot the gentoo live image. Can I get it to save settings every time I shut down, like a regular install?

---

### Post by trimeta on 2008-06-10
Probably not; the way most CD-based live distros work is by storing a compressed copy of the file system, and decompressing it on the fly at run time. LiveUSB installs do the same thing. Only when the distro has made specific efforts at persistent live installs, such as Ubuntu's casper system or Knoppix's persistent home thing, can you actually save changes.

---

