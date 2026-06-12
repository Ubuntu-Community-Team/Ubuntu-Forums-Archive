---
title: "grub fails to install to MBR"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by javaslave on 2009-01-19
Strange problem: GRUB does not install to MBR after installation from either ubuntu or kubuntu (8.10), and does not install to MBR if grub is manually installed from a console after a live CD boot (using the root (hdX,Y); setup (hd0) sequence as per grub manual).

my HDD setup, all drives are SATA:

hd0 (sda):
200GB NTFS (/data)

hd1 (sdb):
100GB ext3 (/usr/local)
100GB ext3 (/home)

hd2 (sdc):
350GB ntfs (win XP; /xp)
145GB ext3 (/)
5GB swap 

note1: GRUB *does not* report a failure - it claims to have successfully installed to the MBR each time.

note2: my BIOS does not have any auto virus checker that could be stopping the MBR write

lastly, the only other thing i've done that may be relevant is that i deleted an ext3 partition from hd0 and resized the remaining ntfs partition to span the disk using GParted, after which i had to reinstall the NT bootloader from an XP recovery console with fixmbr.

just trying to get linux to boot now...

---

### Post by ajgreeny on 2009-01-19
Which partition is your boot partition, are you sure it's hd0?  Run ```
sudo fdisk -l
``` from the live CD if you can't get into your installed version and see which partition has the * against it, then run setup (hdx,x) to fit in with that, remembering that fdisk reports as sda, sdb etc etc, and you need hdx for grub.

---

### Post by javaslave on 2009-01-19
thx for reply.

unfortunately am on my Mac OS X laptop at work, cannot post the output of fdisk.

linux /boot is on (hd2,2), and that's what i ran in the root (hd2,2) -> setup (hd0) sequence. As i understand it, (hd0) is grub-code for the MBR.

---

### Post by caljohnsmith on 2009-01-19
> **javaslave said:**
> thx for reply.

unfortunately am on my Mac OS X laptop at work, cannot post the output of fdisk.

linux /boot is on (hd2,2), and that's what i ran in the root (hd2,2) -> setup (hd0) sequence. As i understand it, (hd0) is grub-code for the MBR.
It doesn't look like "setup (hd0)" will work in your case, because (hd0) is your sda data drive. Are you booting the Windows sdc drive I would assume? Since Ubuntu is also on that drive, try instead:
```
sudo grub
grub> root (hd2,2)
grub> setup [COLOR="Blue"](hd2)[/COLOR]
grub> quit
```
And then you should get the Grub menu on start up. How about giving that a shot and let me know how it goes.

---

