---
title: "Help Nothing Works!!!!"
date: 2005-12-05
forum: General Help
---

### Post by Anomaly on 2005-12-05
Hi, I desperatly need your help!!!

I was trying to get linux to view another hard drive partition via the disks option.

first I selected the disk partition, put the path as /home/marco then I enabled it.

as soon as I quit the disks app I couldnt do ANYTHING not even open the terminal, I logged out and when I tried to log back in, It told me That I had no permissions and that I should open ubuntu in "safe" mode to try and sort out the problem.

Any ideas on reversing the problem are greatly appreciated! Thanks!!

---

### Post by Qrk on 2005-12-06
Next time, make a folder in your /home/marco directory, say, 

/home/marco/partitionX

and tell the system to mount the partition there. 

as to your problem now I don't have a great answer. If your /home/marco still exists with your home data, then you might just be able to change the permissions back in safe mode. If you managed to delete it... I think it might be easiest to reinstall. Someone with more experience than I might be able to help you more.

---

### Post by cilynx on 2005-12-06
What you did is mount the partition that you wanted to look at over your home directory.  Thus all of your settings, preferences, and data were covered up by whatever was on that partition.  A reboot should take care of getting you back where you were without the extra partition mounted.  Don't worry, your home directory is safe.  As previously stated, make an empty directory to mount extra partitions in.

Good Luck

---

### Post by Anomaly on 2005-12-06
Thanks ALOT! As soon as I get some free time I'll try what you've said!!

---

