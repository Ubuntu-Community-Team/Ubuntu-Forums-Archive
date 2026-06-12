---
title: "Laptop install - no cd, floppy or net conn"
date: 2005-10-04
forum: Hardware &amp; Laptops
---

### Post by h0me5k1n on 2005-10-04
I'm trying to install ubuntu on a sony vaio laptop with no cd (except a pcmcia one which is not bootable from the bios), no floppy drive and no network connection.

I was under the impression that I can install ubuntu onto the laptops hard drive using a desktop pc with a 'normal IDE' to 'laptop IDE' converter and then switch the hard drive into the laptop once installed and boot to it.

Grub starts fine but when it attempts to boot linux in the laptop but I get the following error:

/bin/sh: error while loading shared libraries: libc.so: cannot open shared object file: no such file or directory 
kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)

If I put it back in the desktop it was originally installed from it works fine.

Any ideas on how to install ubuntu in a desktop PC then transfer the hard drive to the laptop.......  or is there another way to install it? 

I was thinking I could maybe put a 'floppy bootdisk' install (of win98 with cd/pcmcia support maybe) on a small partition, boot to it using grub and then run an install cd (either from the cd or copied onto another partition of the drive) from there? (big emphasis on the maybe!!)

---

### Post by mr_mop on 2005-10-04
Check this, it may help.
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

I installed MS DOS 6 instead of windows which is quicker.

---

### Post by h0me5k1n on 2005-10-04
thanks for the link but the guide details how to install if you already have windows running but my hard drive is blank - which is why I have to use another  pc to install the os files.

unless there is another way...?

---

### Post by mr_mop on 2005-10-05
I guess I am lucky in that I have DOS 6 knocking about from years ago.  If you could download something similar, [http://www.freedos.org/](http://www.freedos.org/) for example it may help you out?

the problem with installing on one machine and moving to another is that if the 2 machines are not identical, then the drivers are all going to be wrong.

---

### Post by h0me5k1n on 2005-10-05
yeah - I suppose but I was hoping to install the base packages and then swap the drives over for the detection to be done but it wouldn't work.

Thanks again

---

