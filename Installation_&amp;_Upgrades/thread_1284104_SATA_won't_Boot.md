---
title: "SATA won't Boot"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by Dave.Wynne on 2009-10-06
I'm using old hardware whose BIOS does not have an option for SATA boot, it just checks CDrom, A, C etc. I've installed a SATA card and installed 9.04 server on RAID 1 SATA hard drives. Can I create a boot CD to allow me to start the system? And if so how?

Dave Wynne

---

### Post by pmlxuser on 2009-10-06
if you manged to install on it a live boot should be able to get you there.

however have you tried installing grub on the computers ide disk. since your computer is able to read from the ide disk thenm installing grug on it will give you a bootable option you can just edit the root system partition so that grub searches it on your sata disk.

---

### Post by Dave.Wynne on 2009-10-06
Thanks for the answer but I'm a bit of a newbie and don't understand. What is a live boot and how can I install grub onto an ide disc so it searches for my sata disk?

---

