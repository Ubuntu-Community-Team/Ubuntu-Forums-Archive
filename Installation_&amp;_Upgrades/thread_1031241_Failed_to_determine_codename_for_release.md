---
title: "Failed to determine codename for release"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by atisss on 2009-01-05
I've found an issue in [http://ubuntuforums.org/showthread.php?t=427943](http://ubuntuforums.org/showthread.php?t=427943) but as i'm new to this forum i don't understand how to reply to it :)

Anyway i hope this helps someone.

I tried installing Ubunut 8.10 from Alternate CD. 

After RAID setup i got debootstrap error:  Failed to determine codename for release

So, the solution to this was to open another terminal (F2) and re-mount cdrom, as it's device name has been changed.

#mount
(see what's device name for current /cdrom)
(i had /dev/scd0 mounted on /cdrom)
#umount /cdrom
#mount /dev/scd[TAB] /cdrom
(enter your device name without number, from previous output of mount, and TAB autocompletes it with correct number)

Then just return to installer (F1), return to install options menu and choose "Rescan CDROM"

---

### Post by lenzj on 2009-01-06
That worked for me as well.  It must be a bug unique to raid installs.  Thanks for the post!

---

### Post by rwhite1 on 2009-01-31
This worked for me up to the last step. I also had /dev/scd0 mounted to cdrom. It failed to remount, but going back to the installation menu, physically opening and closing the cdrom drawer (so it would attempt to read the volume) and rescanning the cdrom did the trick. After that I went back to the base system installation without issue. 

Notes: Ubuntu 8.10 i386
            verified download with md5 utility, burned onto CD and then reverified the CD after burning on a different computer.
            read in another forum that a guy thought this was from a bad sector on the physical drive (this is an old machine so I suppose it's possible)

---

