---
title: "GRUB error 25 on usb ubuntu persistent install"
date: 2008-09-15
forum: General Help
---

### Post by smvtsailor on 2008-09-15
I've been trying unsuccessfully to run Hardy on my usb drive as a Live USB with persistence.  I followed the instructions [>here<]("http://ubuntuforums.org/showthread.php?t=575406"), except i used the Hardy .iso and changed all instances of "Gutsy Gibbon" to "Hardy Heron" in the menu.lst that was supplied.  When I boot from the USB, I get to GRUB stage 1.5, and then get Error 25.  I've tried a search, but none of the scenarios seemed to be the same.  How do I fix this?  Thanks!

---

### Post by smvtsailor on 2008-09-15
If it matters, I am using a PNY 8G flash drive.  I am using a Dell Dimension 8300 with Pentium 4 processor.

---

### Post by smvtsailor on 2008-09-15
Anyone know what could be wrong?

---

### Post by DOSIX on 2008-09-15
what was the text that appeared with the error. check the grub manual, it should list all the error there. if you supply this info, i should be able to help you, i am running it off a usb right now. (installed onto the usb 8 gigs)

---

### Post by smvtsailor on 2008-09-15
It only said:

GRUB Loading stage1.5.

GRUB Loading, please wait...
Error 25


Then it just sits there.  Error 25 is documented as "This error is returned if there is a disk read error when trying to probe or read data from a particular disk."

---

### Post by smvtsailor on 2008-09-15
Anyone know what could be wrong?

---

### Post by smvtsailor on 2008-09-15
bump

---

### Post by phidia on 2008-09-15
Error 25 means grub couldn't read data from the drive. 
At the grub commandline (grub>) enter  > find /boot/grub/stage1
then enter > root
Both those commands should find your install partition. At this point you would normally enter "setup hdX,Y" or just "setup hdX" if grub is loading from MBR rather than a root partition. 
Since I don't know the specifics of your install I can't tell you the exact way to complete it but those commands can setup grub. 

You should also look for mismatches between your fstab and the usb drive, but I don't think that would result in the error you got.

---

### Post by caljohnsmith on 2008-09-15
From your Live CD, try doing:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Reboot, and then let me know what happens on start up.

---

### Post by smvtsailor on 2008-09-16
Below is the output of running setup.  I'm about to try to reboot.




 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,1)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,1) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

---

### Post by caljohnsmith on 2008-09-16
> **smvtsailor said:**
> Below is the output of running setup.  I'm about to try to reboot.




 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 [COLOR="Red"](hd1,1)[/COLOR]"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 [COLOR="Red"](hd1,1)[/COLOR]"... failed (this is not fatal)
 Running "install /boot/grub/stage1 [COLOR="Red"](hd1,1)[/COLOR] /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
I all ready see a problem. You used "setup (hd1,1)", which is not going to install Grub to the MBR; it will instead install it to the partition boot record (PBR) of sdb2. What was the output of the "find /boot/grub/stage1" command?

---

### Post by smvtsailor on 2008-09-16
Now, I'm getting the same thing as before, but it is now error 18.  According to the GRUB manual, this means:

18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Could my hardware be the problem?  The computer is about 5 years old.

---

### Post by smvtsailor on 2008-09-16
Its working, i tried it on a different computer.  It turns out it was the bios being stupid.

---

