---
title: "Proper install of 9.04 using seperate /root and /home partions?"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by Maximilian Maksutovic on 2009-06-12
I have had a tremendous amount of success running my Macbook Pro 4.1 dual-booted with Ubuntu 9.04 (EXT4). I was told from reading the literature that it is a good idea to have one's own partions as such:

/root @ ~5 gigs
/home @ ~most of your disk space  
/swap @ ~double your ram

I partitioned the disks accordingly, had some fun with a very high functioning Ubuntu (the Macbook pro seems to like it very much :) ) However, it seems that EVERYTHING is getting written to the / drive, so now i get error messages such as ```
dpkg: failed to write... no space left on device
```(the *device* being my / drive) of course while my /home partition has 50 gigs left! I am about to do a clean install however i wanted to get the proper information in partitioning so that I do not have this problem again.

Is it better to just have one solid / drive and a swap? I have scoured these forums and others for a possible solution or advice and I haven't found an article relating my problem-- so i apologize if this is a common problem. Thank you in advance for your help!

FYI: here are some outputs from terminal regarding my partitions (they don't make much sense to me, maybe why i am having problems?:

```
maxi@maxi:~$ df -Th | sort
/dev/sda1     ext4    4.6G  3.7G  666M  86% /
/dev/sda6     ext4     50G   14G   34G  28% /home
Filesystem    Type    Size  Used Avail Use% Mounted on
lrm          tmpfs    998M  2.4M  995M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs        tmpfs    998M     0  998M   0% /lib/init/rw
tmpfs        tmpfs    998M   84K  998M   1% /dev/shm
udev         tmpfs    998M  168K  998M   1% /dev
varlock      tmpfs    998M     0  998M   0% /var/lock
varrun       tmpfs    998M   96K  998M   1% /var/run

```

---

### Post by merlinus on 2009-06-12
If you will be installing lots of apps, then 5G is clearly not enough for /.  I suggest taking space from /home and increasing it to 10-15G, or even 20.

Also, if you have 2G or more of ram, then /swap can be 1.5G.

---

### Post by Maximilian Maksutovic on 2009-06-12
Thank you very much merlinus. I will try that and see what happens! Would you (or anyone else) mind explaining why this is? When you install an app, is it installed in the root drive, or are all the files associated with the app there? I guess I am simply not clear on how the separate partitions work yet (i do understand that the /root and /home is good if you want to reinstall a distro without deleting you data. Are there better reasons for having the two partitions?)

---

### Post by merlinus on 2009-06-12
/ (root) is where the system files and most applications reside.  When you install a newer version, or reinstall, that partition is reformatted.  

That is why having /home is useful for storing data, and configuration and setup files for most apps, and some for the os, reside there as well.

When upgrading or reinstalling, select the mountpoint (/home) for that partition, but DO NOT format it, and nothing is lost.

---

### Post by Chemical Imbalance on 2009-06-12
I agree that 5gb might not be enough for /.  I personally use 20gb.

---

### Post by Maximilian Maksutovic on 2009-06-12
Thank you merlinus & Chemical Imbalance - I have just reinstalled and everything is working fine. Now understanding the root partition better, i understand why i had the problems. Thanks again!

---

### Post by merlinus on 2009-06-12
Glad it is working.  Post back if you run into difficulties, and happy ubuntuing!

---

