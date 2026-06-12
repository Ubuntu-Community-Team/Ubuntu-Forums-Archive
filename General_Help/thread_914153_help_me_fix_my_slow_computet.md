---
title: "help me fix my slow computet"
date: 2008-09-08
forum: General Help
---

### Post by maximuss77 on 2008-09-08
hello sorry if the answer is somewhere else in this forum but i did look and i cant find the help windows free in june i have had no trouble untill recently i rebooted my computer and got an error 17 message on my boot up so after reading the forum on here i found some help saying something somehow unconfigured my harddrives and i had to change the bios settings i looked around there for a bit but decided to just use my respawn disks (i have alienware comptuer so it made my computer back to how i purchased it) i put ubuntu right back on computer but now my computer constantly "lags" it feels like im playing a video game on a slow internet connection... could this have something to do with that error i got... i have 4G ram so i dont think thats the issue ..any help would be greatly appreciated to at least get me looking in the right direction

---

### Post by Rocket2DMn on 2008-09-08
> **maximuss77 said:**
> hello sorry if the answer is somewhere else in this forum but i did look and i cant find the help windows free in june i have had no trouble untill recently i rebooted my computer and got an error 17 message on my boot up so after reading the forum on here i found some help saying something somehow unconfigured my harddrives and i had to change the bios settings i looked around there for a bit but decided to just use my respawn disks (i have alienware comptuer so it made my computer back to how i purchased it) i put ubuntu right back on computer but now my computer constantly "lags" it feels like im playing a video game on a slow internet connection... could this have something to do with that error i got... i have 4G ram so i dont think thats the issue ..any help would be greatly appreciated to at least get me looking in the right direction

Please edit your post to use complete, logical sentences, nobody is going to filter through that mess to try and figure out what your actual problem is.  Thank you.

---

### Post by maximuss77 on 2008-09-08
sorry i guess my problem is since i had to reinstall ubuntu on my computer it has been extremely slow not just the internet but even opening basic applications

---

### Post by maximuss77 on 2008-09-08
i guess i did a very bad job explaining what my problem is... everything was running very fine on my computer then i got an error 17 on boot up, rather than fix it i just deleted my computer and reinstalled ubuntu now everything is running extremely slow... any help would be greatly appreciated thanks

---

### Post by Rocket2DMn on 2008-09-08
Did you tell the installer to use the entire hard drive when you did the installation?  If not, you may just be extremely crunched for space.  Please post the output of this command so we can see your partitions:
```
sudo fdisk -l
```
It's possible that your hard drive is dying.

---

### Post by maximuss77 on 2008-09-08
maximuss@maximuss-desktop:~$ sudo fdisk -l
[sudo] password for maximuss: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd310d310

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29171   234316026   83  Linux
/dev/sda2           29172       30401     9879975    5  Extended
/dev/sda5           29172       30401     9879943+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00e697ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6052    48612658+   7  HPFS/NTFS
/dev/sdb2            6053       60801   439771342+   5  Extended
/dev/sdb5            6053       59570   429883303+  83  Linux
/dev/sdb6           59571       60801     9887976   82  Linux swap / Solaris

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x465232c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001    c  W95 FAT32 (LBA)

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001    7  HPFS/NTFS
maximuss@maximuss-desktop:~$

---

### Post by maximuss77 on 2008-09-08
i posted what i saw in terminal is there a way to tell if it is my hard drive failing based on this info thanks for the help

---

### Post by Rocket2DMn on 2008-09-08
Unless a hard drive you know is in there fails to appear, we can't really make any judgements as to the health of the drive based on what we are seeing.  If you ever get notices from SMART doing bootup, that would definitely be a problem.

I see that you have two linux installs - is this intentional?

---

### Post by maximuss77 on 2008-09-08
no it was not intentional i get a screen on startup of a bunch of script running and i see things like checking and stuff it runs through to fast for me to read tho that what you mean when you said SMART running? thanks for the help

---

### Post by Rocket2DMn on 2008-09-08
If you aren't seeing anything about SMART, then I suppose that is good (it is a system put onto hard drives that is intended to sometimes know when the drive is on the brink of failing).
Since you just did an install, you may find it easier to go to the LiveCD, delete the linux partitions that you have created (seems you have 2 installs), and start fresh.  This still doesn't really explain the lag though you are experiencing though, can you elaborate on the lag?  Is it the stuff happening on the screen that is is slow, or is the computer slow to boot?

---

### Post by maximuss77 on 2008-09-08
can you walk me through how to delete one of the installs through the live cd and it is both slow boot up and slow at running things thanks for the help

---

### Post by Rocket2DMn on 2008-09-09
If you are going to delete both installs and start over, first back up everything that might be important to you.  Then boot from the LiveCD, go to System->Administration->Partition Editor.  In the upper right you can choose the disk (sda, sdb, sdc, sdd, etc).  You will want to delete the linux and swap partitions (ext3 formatted and swap formatted) partitions that exist, probably on sda and sdb.  If it complains about swap being mounted, right click that tiny area in the little colored graph and click unmount, then try deleting again.  This means you will probably delete sda1, sda2, sda5, sdb2, sdb5, sdb6 (NOT sdb1 - this looks like a windows install or data partition).  When you are POSITIVE you have the right stuff deleted, commit the changes, then proceed to install.
During the install process you need to make sure it installs the partitions how you want - probably install to the sda disk (which should at this point be empty).
If you have any questions during this process, take a screenshot and post it here - don't do anything you aren't comfortable with, esp. when it comes to deleting partitions.

---

### Post by Camilia on 2008-10-28
My boot up is slow.
Is there anything wrong here?

Partition 1 has different physical/logical endings:
     phys=(83, 5, 63) logical=(84, 4, 52)

This looks strange. Is this normal?

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f565f56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9847    79095996   83  Linux
/dev/sda2            9848       10011     1317330    5  Extended
/dev/sda5            9848       10011     1317298+  82  Linux swap / Solaris

Disk /dev/sdf: 16 MB, 16412672 bytes
6 heads, 63 sectors/track, 84 cylinders
Units = cylinders of 378 * 512 = 193536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          85       15996+   1  FAT12
Partition 1 has different physical/logical endings:
     phys=(83, 5, 63) logical=(84, 4, 52)

I don't have a Partition Editor could it be listed as something else?

---

