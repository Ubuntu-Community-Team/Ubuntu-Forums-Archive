---
title: "Install grub/lilo from live DVD?"
date: 2006-01-06
forum: Installation &amp; Upgrades
---

### Post by tyraen on 2006-01-06
Hi everyone,
Well, the installation died (during debootstrap, I guess maybe the disc is bad?), unfortunatly I was trying to create a dual boot environment with XP.  Now I have no bootloader and can only boot off CDs.  What I'd like to do is install either grub or lilo from the Live disc, but I can't quite get it to work.  Grub is apparently already installed (I guess on the Live disc) and I don't know how to move it to the MBR.

Any help would be great!
Thanks!

---

### Post by benco on 2006-01-06
Before trying to reinstall, you should restore your MBR.
You can do that with a DOS floppy and at prompt type fdisk /mbr or a Windows XP bootable CD in rescue mode and type fixmbr.

---

### Post by tyraen on 2006-01-06
Well, I was looking for a way to do it from Linux since I didn't have XP discs with me at the time.  Anyways, fixed now.

Thanks,
Nick

---

