---
title: "My windows XP dual boot just disappeared"
date: 2008-10-18
forum: General Help
---

### Post by ermesomega on 2008-10-18
after this recent update, my dual boot menu doesn't have WindowsXP as a bootable OS.  I dunno where it went.  Anyone else having similar problems?

---

### Post by mikewhatever on 2008-10-18
Please post the output of <sudo fdisk -l>.

---

### Post by Sef on 2008-10-18
> Please post the output of <sudo fdisk -l>.
That's a small L.  Most likely something happened to GRUB.   If you see a NTFS partition, then get [supergrubdisk]("http://supergrubdisk.org").  It will reinstall grub.

---

### Post by cyclobs on 2008-10-18
you've more then likely changed the grub list and moved your windows boot to the top of the list which is a no no cause it will be wiped when a new kernal update is made..

next time use the default boot option near the top of the page.


and to fix your problem just copy the ubuntu boot code and change it to suite windows.

usally just takes pointing it to the right partition ;)

---

### Post by ermesomega on 2008-10-20
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433        2724     2345490   82  Linux swap / Solaris
/dev/sda3   *        2725        4069    10803712+   7  HPFS/NTFS

---

### Post by caljohnsmith on 2008-10-20
It looks like Windows is on sda3, so to add it to your Grub menu, first open a terminal (applications > accessories > terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom of that file add:
```
title Windows XP
root (hd0,2)
chainloader +1
```
Reboot, try the Windows entry in the Grub menu, and let us know if it works. :)

---

### Post by ermesomega on 2008-10-20
is there any way I can alter my grub menu as is to have my bootable OS's?  The way I had it setup before, all I had to do was alter a'lil bit of code and I could chose at start up.  Can I relive my simpler days of past? or do I really need to download some program?

---

### Post by Miljet on 2008-10-20
I haven't seen any reply that asked you to download (or install) anything. All the replies are doing is trying to help you repair your menu.lst file to get back to where you were before.

---

### Post by ermesomega on 2008-10-21
Yes, you are correct.  I altered the GRUB menu and got my windows dual boot back.  Thank you all for your assistance.
Cheers

---

