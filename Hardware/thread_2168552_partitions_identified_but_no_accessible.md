---
title: "partitions identified but no accessible"
date: 2013-08-18
forum: Hardware
---

### Post by caiorrs on 2013-08-18
Hi there,

my 1TB HD is full of documents, photos and etc important files. It has stopped working correctly a while ago.
it has 4 partitions, but just 1 is accessible, in GParted it is divided on 4 partitions, all of them NTFS, but 3 out of 4 has a exclamation sign in the side (partition division).
I would like to know how to recover these partitions. In GParted when I enter in properties of each partition it returns me 

[ATTACH=CONFIG]245451[/ATTACH][ATTACH=CONFIG]245452[/ATTACH]

please, thyere are VERY IMPORTANT FILES THERE!!

thank you

---

### Post by caiorrs on 2013-08-18
please help D=

---

### Post by carl4926 on 2013-08-18
In Gparted: Right click the partitions in question and > check

---

### Post by Mark Phelps on 2013-08-19
The error messages are telling you to run CHKDSK, and unfortunately for you, there simply is no Linux equivalent of CHKDSK.  There is ntfsfix, but that addresses only trivial errors, and is not a CHKDSK equivalent.  However, running CHKDSK, especially on corrupted partitions, is likely to "erase" the very files you need.

So, you need to consider whether or not you want to do file recovery BEFORE running CHKDSK.  If you do, then read on ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

Once you've doine file recovery, if you have Windows on your PC, and can boot into it, then run CHKDSK on each of the partitions. If you can't boot into Windows on your PC, you will need to remove drive and connect it to a Windows PC and run CHKDSK there.

---

