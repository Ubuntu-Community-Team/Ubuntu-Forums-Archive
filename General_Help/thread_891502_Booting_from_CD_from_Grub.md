---
title: "Booting from CD from Grub"
date: 2008-08-16
forum: General Help
---

### Post by tdw197 on 2008-08-16
Hi all,

I have finally managed to get xubuntu installed on an old laptop i had, difficult as the Bios seems to be corrupt and I can't change it to boot from cd.

I got round this by using a combination of the alternate Xubuntu CD and ISO with unetbootin, then formatted the lot and did a complete fersh install - and its great!

However I would like to have some sort of failsafe mechanism and someway of booting live cds to test other distros.  I found this:

[http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB#Smart_Boot_Manager](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB#Smart_Boot_Manager)

Which seemed perfect, and did exactly what i wanted - boot cds from grub!

I set it up, pretty much as the link, but modded my menu.lst by putting the following at the end:

title    SBMBoot a CD
root     (hd0,0)
kernel   /boot/memdisk
initrd   /sbm.bin

However, when I boot and choose the above option in grub, I get "Error 23: error while parsing number"

Anyone have any ideas, as the limit of my knowledge (and googling) was past a while back - or if not, is the any other way of booting a cd from GRUB?

TIA

---

### Post by linux_tech on 2008-08-16
Did you try a super grub disk?
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/SuperGrubDisk](http://www.supergrubdisk.org/wiki/SuperGrubDisk)

---

### Post by tdw197 on 2008-08-16
> **linux_tech said:**
> Did you try a super grub disk?
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/SuperGrubDisk](http://www.supergrubdisk.org/wiki/SuperGrubDisk)

Ta for the idea, but I did briefly look into it before.

Isn't Super Grub a bit like a live cd, you need to be able to boot from cd to get into it?  which is exactly what i can't do and want to.  Plus from a quick glance I can't see an option on super grub to boot from cd anyway, even if I could load it.

Though I'm more than happy to be proved wrong (please!)

---

### Post by BrandonBmx on 2008-08-16
try pressing different keys on startup:
like i press F2 for device selection (then after i press c to boot from CD i didnt change the bios bootup order

---

