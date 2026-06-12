---
title: "re-installing grub to Raid0"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by Stonebot on 2009-10-02
Hi,
I have Ubuntu 9.04 and have just installed Windows 7 to a 100gb partition.

This is all under 1 raid0 array. The Ubuntu partition with 400gb and Windows 7 100gb (approximately).

I am trying to re-install grub since when I installed windows 7 it completely ate up the Grub Bootloader.

I have live booted Ubuntu 9.04 and entered sudo grub. Then "find /boot/grub/stage1" it returns "Error 15: File not found"

I have read that if I remove the /boot/ it will work but when i enter the "find /grub/stage1" it returns "Error 15: File not found"

Anyone know how to get Grub on raid0.

Thanks :D
Stonebot

---

