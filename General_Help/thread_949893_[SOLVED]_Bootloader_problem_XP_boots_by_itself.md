---
title: "[SOLVED] Bootloader problem: XP boots by itself"
date: 2008-10-16
forum: General Help
---

### Post by sendHalp on 2008-10-16
Hello all,

After running a partition resizer utility and installing XP on my harddisks second partition, windows now boots by itself and I no longer see the GRUB menu.

How can I fix this?  I know ubuntu is still on my other partition, but I can't get to it.

---

### Post by Ms_Angel_D on 2008-10-16
You have to restore grub Windows automatically overwrites it.

[LOOK HERE]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5")

---

### Post by sendHalp on 2008-10-16
Many thanks for the link.  I hope I can do this with an opensolaris livecd, I can't find my ubuntu one since I cleaned up my office.  =)

---

### Post by kodalisrikanth on 2008-10-16
> **sendHalp said:**
> Hello all,

After running a partition resizer utility and installing XP on my harddisks second partition, windows now boots by itself and I no longer see the GRUB menu.

How can I fix this?  I know ubuntu is still on my other partition, but I can't get to it.


See this. This is my personal experience.... [:)]

[http://kodalisrikanth.blogspot.com/2007/04/fixing-grub.html](http://kodalisrikanth.blogspot.com/2007/04/fixing-grub.html)

---

### Post by TeXtonyx on 2008-10-16
You can load the Ubuntu partition with Super Grub. It is not a
large download and can be very handy. Once you boot to Ubuntu
you can reinstall grub from there. I use Super Grub with the
Help option which explains things as you go.

Look at your /boot/grub/menu.lst 
It needs to have have an entry for XP
similar to the commented example earlier 
in that file. You want an uncommented entry for XP.

---

### Post by sendHalp on 2008-10-16
Super grub disk did the trick, unfortunately grub on the live cd wasnt mounting hd0 as instructed by the help page.

---

