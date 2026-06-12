---
title: "Pcmcia"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by hellstern on 2007-06-24
Hi,
I want to install a version of AstLinux(Asterix) on a 1 gb Compact Flash card. I have a PCMCIA Compact Flash card reader. The version of Ubuntu is 7.04 and the laptop is a IBM X41.

I have done: *sudo fdisk -l* and gets this result:

[I]    Device Boot      Start         End      Blocks   Id  System
    /dev/mmcblk0p1               1         984     1983619+   6  FAT16[/I]

Then I wants to run this command: 

  * sudo gunzip -c AstLinux-0.4.5-net4801.img.gz > /dev/mmcblk0pl*

Then I get: bash: [I]/dev/mmcblk0p1: Permission denied
[/I]

I don't know if bash: /dev/mmcblk0p1 is the right device or how to get around the permission problem. I can do this on a Windows PC but I wants to learn how to do it in Linux – Ubuntu so any help is received with thanks :-)

/Tue

---

