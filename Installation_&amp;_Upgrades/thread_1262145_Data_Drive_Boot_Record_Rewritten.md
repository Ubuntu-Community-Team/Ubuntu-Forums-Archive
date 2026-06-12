---
title: "Data Drive Boot Record Rewritten"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by moe458 on 2009-09-09
Hi,

Issue:
I need to repair my data drive (/dev/sda1) windows dynamic volume on which I wrote my grup when installing Ubuntu 9.04.  I know the data is intact.(reason i'll share with u in a bit).

Senario:
What was I doing?

I was trying to reinstall ubuntu due to wrong installation of the drivers and I was not able to fix. bad idea
I went thru the manual partitioning of the drive on Disk /dev/sdd: 20.4 GB (that was fine).  After I went into advance and installed grub boot loader on the Disk /dev/sdb: 320.0 GB, which started bunch of issue not being able to read the volume in windows (showing raw volume).  What it had done was it created extended volume with /dev/sdd and placed the boot loader files with ubuntu and rest of the drive was showing 180 gig as /dev/sda1. Grub was giving me error 22 and error 15 i believe. 

320 GB HD was a windows dynamic volume with bunch of my data and I quite believe that it's still there.  Just not sure how.

all volumes were unaccessible. After spending the whole night i did the following:
I reinstalled ubuntu by unplugging the rest of the drives and and it started to work just fine and detecting windows etc. no problems.

I just need to fix that paticular drive and I need some help with it. Please help me thank you !!


```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321   42  SFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641   42  SFS

Disk /dev/sdc: 30.0 GB, 30020272128 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3649    29310561    7  HPFS/NTFS

Disk /dev/sdd: 20.4 GB, 20416757760 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        2373    19061091   83  Linux
/dev/sdd2            2374        2482      875542+   5  Extended
/dev/sdd5            2374        2482      875511   82  Linux swap / Solaris

```

---

### Post by moe458 on 2009-09-09
just to add i checked in gparted and it's showing me the below information:

[IMG]http://i671.photobucket.com/albums/vv73/mqueue_2009/Screenshot.png[/IMG]

---

### Post by moe458 on 2009-09-09
And yet after 21 hours of trying every deadly truck in linux, there was no fix.  

Windows have managed to do so with in a couple of hours.  The data has been recovered.

As i had intially thought. Only the boot record of the NTFS data drive was overwritten by grub.  When i had when into advance settings and changed the boot loader option to this drive.

Solution:
-unplugged the drive overwritten drive.  
-reinstall the linux on the correct drive w/ dual boot with windows (sdc1) / ubuntu (sdd) leaving sda1 along unplugged   during installation.
-checked both OS are working fine.
-load windows (in my case xp)
-installed Power Data Recovery in xp
-it read the drive and started recoving all the stuff. :guitar:

I'm sure there are other tools available for windows to recover the data off the drive, however i was not sucessful with ubuntu to recover the data or volume.

**[SIZE="4"]Issue resolved !![/SIZE]**

---

