---
title: "installing an NTFS partition"
date: 2008-11-08
forum: General Help
---

### Post by zero777zero on 2008-11-08
i was dual booting m$ and ubuntu together until a couple days ago when grub went haywire and wouldnt let me log into either, so i re-installed 8.10 over the whole drive. now i need to reinstall windows but when i boot from the install cd it says i have "no hard drive". i have been told that this is because i need to partition the beginning of my drive with ntfs. so i try to do this with gparted which gets me nowhere.

---

### Post by Vadi on 2008-11-08
I was having this issue too actually.

Decided to just install windows first and then ubuntu after as windows was fcking up the bootloader each time.

---

### Post by geirha on 2008-11-08
I assume the install CD that says you have no hard drive is the Windows install CD? If so, it sounds like the Windows CD doesn't have the correct drivers for the harddrive controller. Try going to the website of the PC-manufacturer and see if they have drivers for that Windows version.

---

### Post by Vadi on 2008-11-08
Ahh yes, it's actually what geirha said. The setup disk doesnt have the driver for your harddrive and it can't see it.

---

### Post by zero777zero on 2008-11-08
that makes sense since my laptop originally came with vista

---

### Post by zero777zero on 2008-11-09
turns out i can't even install vista. however the vista install was more specific, needs to have a windows filesystem on the first partition in order to install! too bad when grub freaked out a few days ago i had to install ext3 over the whole hard drive when i reinstalled ubuntu.

i need a way to make a new partition (ntfs or fat32) but gparted wont let me do this...

---

### Post by geirha on 2008-11-09
gparted can't resize and move partitions on a drive if the drive is in use, so you need to run gparted from a live CD, like the ubuntu CD.

---

### Post by zero777zero on 2008-11-09
alright, i booted up the hardy heron install disc ([couldnt use 8.10]("http://ubuntuforums.org/showthread.php?t=966436&page=4"))

here is the configuration i set for my new partition

1.fat32 /windows primary beginning
2.ext3 / primary beginning
3.swap area /swap logical end

note it wasnt an option to ntfs to i used fat32

tried to install windows and it still does not recognize hardware

here's what it looks like now in gparted

[http://img376.imageshack.us/my.php?image=screenshotji1.png](http://img376.imageshack.us/my.php?image=screenshotji1.png)

---

### Post by geirha on 2008-11-09
Are you sure the CD you have is an install CD and not a recovery CD? I think it's common to ship a recovery CD with laptops now a days, and that the recovery CD requires that certain parts of the initial install is still there.

---

### Post by zero777zero on 2008-11-09
yea its an install cd

it gives the option to "recover" but it also gives the option to "install"

---

### Post by Vadi on 2008-11-09
Un recognize hardware = no drivers for your harddrive on the disk. Has nothing to do with partitions or having an ntfs one.

I'd try a different disk, that helped me.

---

### Post by TeXtonyx on 2008-11-09
Remember to make backups. Wipe all the partitions off the hard drive. 
Reinstall Vista to the whole drive. Then use Vista to resize/shrink
the Vista partition. That shrinkage will become the size of your
Ubuntu partition. Some Vista cds will upgrade, other will only install
to the whole hard drive. Reinstall Ubuntu: choose 'largest free
space (guided' which will avoid the rare gparted resizing errors.
If you are confident, you can choose the manual method.

At Step 7, Advanced, choose install grub to the /boot partition.
Ubuntu will not boot yet. Download Easybcd and add Ubuntu to the
Vista bootloader (under Linux). The advantage of this method is 
that neither OS depends on the other OS in order to boot. The 
Super Grub Disk will let you boot Ubuntu if Vista-> or its 
bootloader (bcd), fails.
This also really aids in troubleshooting. Gone are the pages/days
spent on trying new menu.lst configurations when Windows won't 
boot, and the problem is in Windows or its boot sector, that 
sometimes gets corrupted when grub is installed to the MBR. 
Easybcd is designed for Windows users. I think early, is the wrong
time for dualbooting new users to tackle the complexities of grub.

The hardest thing to do when changing back from Vista to XP is finding
the right drivers. Those recovery disks come with the right drivers for
the hardware/Vista not XP. If you have a standard Vista install cd, the
drivers for the mainboard are often on another disk that comes with the
system. After installing Vista which will use default drivers, meaning
not nVida video card drivers for instance, you then upgrade the drivers
from the accompanying driver disk. Otherwise, you gotta download them, pita.

---

### Post by zero777zero on 2008-11-10
@ TeXtonyx: i ended up doing something similar. i popped in vista and tried to reformat my fat32 partition to ntfs (since vista needs ntfs). it went through the motions but did not actually reformat it. so i just used vista to delete the whole partition table and i installed vista over everything. then i went back and installed 8.10 (the cd works now after the vista install) and i'm in business! i hope anyone in the future having this problem can shave a day off the time it took me to fix this issue!

---

