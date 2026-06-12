---
title: "[SOLVED] installed ubuntu on new sda, it still tries to boot from faulty sdb HELP"
date: 2008-10-20
forum: General Help
---

### Post by tiggsy on 2008-10-20
I cant get ubuntu to boot, except from floppy

when i booted from original disk, sdb, it kept failing, so i installed ubuntu on the other disk, sda, but it still tries to boot from sdb

i need to get it working. has now been nonfunctional for nearly a day

please somebody help

---

### Post by phidia on 2008-10-20
It sounds like grub is not set up correctly.
Take a look at the Ubuntu wiki guide [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") on reinstalling grub. The guide title is a little misleading as that method will work for many situations.

---

### Post by Ben Miller-Jacobson on 2008-10-20
Try obtaining and using a super-grub-boot-disk to try and boot.

If you either know, or can figure out, what you are doing, you should be able to fix it with the disk as well. Just proceed with caution, because misusing that sort of thing could cause more problems.

---

### Post by tiggsy on 2008-10-21
Right, i did this. 

This is what i did. i was assuming first time through that sda was hd0

```
grub>find /boot/grub/stage1
 
root hd (0,0)
root hd (1,0)

grub>setup hd(0)
```

but that didn't work, it still booted from sdb

then i did the same thing with (hd1)

but the same thing happened.

After a while, i thought i would have a look at the BIOS setup, and there it was starting from disk 2, so i changed that to disk 1, and it now boots from disk 1.

A result.

But it doesn't seem to be finding disk 2 now - so all my data is inaccessible (around 220Gb of stuff). 

This all started by me trying to access disk 2, which was ntfs formatted but had no data. I'm a bit worried about trying to access disk 1 by modding the fstab...

---

### Post by tiggsy on 2008-10-21
Um. The instructions page phidia mentioned includes stuff about a super-grub-boot disk, but it's in the section about windoze, and i no longer have any windows stuff on the computer (apart from an external drive, but as it still writes ok, i'm not fussed about that). Would it still apply?


EDIT: no solution found, ended up reinstalling linux.

---

