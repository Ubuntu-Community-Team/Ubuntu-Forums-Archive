---
title: "cannot mount this partition error"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by n00rt on 2009-05-20
I've just installed ubuntu hardy to an external usb drive - not a flash drive - and when i choose to boot from this device the menu comes up with the choise of operating systems to boot into ie ubuntu, safe mode, memtest etc.. but whichever i choose come up with the error 17 cannot mount this partition.

i did a guided full disk install with grub on the same disk and from what i've read this should work but it doesn't

would a manual install creating a boot partition myself fix this issue or are there any other suggestions?  thanks

---

### Post by albinootje on 2009-05-20
> **n00rt said:**
> but whichever i choose come up with the error 17 cannot mount this partition.


In newer kernels usb sticks and drives are handled the same as IDE, SATA and SCSI disks concerning the device file descriptors.

It is possible that Grub wants to boot /dev/sdb1 instead of /dev/sda1, or the other way around.
You can edit the Grub menu while you're looking at it.
If it wants to boot e.g. /dev/sdb1 edit it to boot /dev/sda1, or when it wants to boot /dev/sda1 edit it to boot /dev/sdb1

See here : [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
> 
You may also want to highlight the 'kernel' line press 'e' to edit and remove the word 'splash' from the end of the line.
After making any necessary modifications you can press 'b' to boot that operating system.
These modifications will not persist across reboots. 


So, use "e" and "b" to make those temporary changes.

---

### Post by n00rt on 2009-05-20
thanks man - got it booted by changing the hd1,0 to hd0,0 - guess i can now change the config to make this change permanent now i'm into ubuntu?

---

### Post by albinootje on 2009-05-20
> **n00rt said:**
> thanks man - got it booted by changing the hd1,0 to hd0,0 

Good.
> 
- guess i can now change the config to make this change permanent now i'm into ubuntu?

Yes, edit /boot/grub/menu.lst accordingly.

---

