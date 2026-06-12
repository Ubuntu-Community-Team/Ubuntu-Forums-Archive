---
title: "No hard drive found during install"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by FrancoisCN on 2009-03-20
I have a brand new computer with a 640GB WD Green HD. P6T Motherboard, i7 920 CPU.

During the install, no hard drives show up in the list at the partionner step. I have googled for solutions and found no answer that fixed it. What I've tried:

[LIST]
[*]fdisk -l returns nothing when running under live session
[*]Unplugged every non essential peripheral hardware (printer, external HD, etc).
[*]Tried Enhanced and Compatible mode for my SATA options in the BIOS
[/LIST]

---

### Post by dstew on 2009-03-20
This might be due to the Linux kernel modules on the live CD being incompatible with your hardware, in particular the disk interface. [Here is a thread]("http://ubuntuforums.org/showthread.php?t=995231") that talks about some of the problems people have seen with this type of motherboard.

It is possible that the kernel on the Live CD won't see your drive, but the kernel on the Alternate Install CD might. I would recommend trying that first.

---

### Post by FrancoisCN on 2009-03-22
It was my bad, I was using my old 8.04 CD instead of my new 8.10 one. The 8.10 detected the HD with no problem. Thanks for the tip!

---

