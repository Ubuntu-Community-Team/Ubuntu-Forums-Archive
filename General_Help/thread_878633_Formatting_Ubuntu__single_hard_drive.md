---
title: "Formatting Ubuntu:  single hard drive"
date: 2008-08-03
forum: General Help
---

### Post by Georgiou on 2008-08-03
Problem: can't format Ubuntu on Hardrive


I have Ubuntu installed on a single drive by it self. I basically wish to delete the partitions and format the 320gbyte hard drive.  formatting Ubuntu off single drive

I tried using the vista setup dvd and xp cd to format the partition but i it didn't work? any ideas??

---

### Post by pooyaplus on 2008-08-03
Hi, is your home folder located on a separate partition or not?

---

### Post by coffeecat on 2008-08-03
You're wanting to delete the Ubuntu partitions on the hard drive, completely erasing the hard drive and creating new partition(s) - correct?

I don't know why the Windows CDs won't do this - perhaps the Linux-formatted partitions are confusing them. Boot up with an Ubuntu live CD. When you get to the desktop, go to System > Administration > Partition Editor. This is Gparted - easy to use. You can delete all the current partitions and create new ones. If you are wanting to prepare partition(s) to install Windows, you can even do this with Gparted, by choosing the NTFS filesystem when you create the partition. If you are wanting a partition to use as a Windows C: drive, make sure it is a primary partition and select the boot flag.

---

### Post by ajgreeny on 2008-08-03
So are you trying to get rid of Ubuntu completely and just use windows on the drive?

If so you first need to restore the windows MBR, and I'm not sure how that's done in Vista.  Secondly you should run the ubuntu live CD, go to System>>Administration>>Partition Editor, delete the ubuntu partitions and then reformat the space left unallocated as ntfs.  You can probably add it to the Vista partition in some way to make one bigger partition, but I'm now so out of date with windows that I'm not sure either if it is possible, or how you would go about doing so in Vista.

If I've got hold of the wrong end of the story and got your intentions all wrong, my apologies; just ignore my ramblings and wait for the correct answer to appear here.

---

### Post by Georgiou on 2008-08-04
> **ajgreeny said:**
> So are you trying to get rid of Ubuntu completely and just use windows on the drive?

If so you first need to restore the windows MBR, and I'm not sure how that's done in Vista.  Secondly you should run the ubuntu live CD, go to System>>Administration>>Partition Editor, delete the ubuntu partitions and then reformat the space left unallocated as ntfs.  You can probably add it to the Vista partition in some way to make one bigger partition, but I'm now so out of date with windows that I'm not sure either if it is possible, or how you would go about doing so in Vista.

If I've got hold of the wrong end of the story and got your intentions all wrong, my apologies; just ignore my ramblings and wait for the correct answer to appear here.


ok, i was able to delete the partitions for Ubuntu.
Now I'm attempting to install xp on the single 320gbyte drive.
However, when i boot from the xp cd,i reach a point in the setup where i get the following message and can't progress any further.

Xp setup error message:

******[A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this stop error screen, restart your computer. If this scren appears again, follow these steps:

Check for viruses on your computer.Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated.
Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical information:
***STOP: 0x0000007B (0xF78D2524, 0xC0000034, 0x00000000, 0x00000000)"]**********


1.Now when i ran the live Ubuntu, i created an NTFS PARTITION. Exited and ran the xp setup......same error message

any ideas???

---

### Post by plucky on 2008-08-04
> any ideas??? 

If your drive is **sata**,then it is probably a sata driver problem and you need to install the sata driver before loading XP.

If you google the error code **0x0000007B** it will take you to microsoft website and show you what you need to do.


Good Luck.

---

