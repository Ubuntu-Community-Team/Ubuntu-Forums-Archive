---
title: "reiserfs recovery"
date: 2008-09-28
forum: General Help
---

### Post by fujikofujio on 2008-09-28
Please everyone I need help recovering my data from a corrupted reiserfs partition. Lately I installed smartmontools and activated smart on that particular hard drive /dev/sdd1

For some reason after restart it shows my drive as unallocated and cannot mount it no more.

After using several reiserfsck command to try and recover it I have still NO luck.

However I know that my data are still there, using ddrescue and foremost it recovered some of it but the filenames are unusable.

Basically after using reiserfsck it gives me a message "bad root block 0", would there be a way to repair the superblock so that I can access my data again?

Please after hurricane ike I don't think I can't take much of this anymore, I'm almost so close to giving up on Ubuntu/Linux, never has this happened to me on windows before that I've lost 80GB of data.

Please help please help...


hamasaki@Ayumi:~$ sudo reiserfsck --check /dev/sdd
reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to [email]reiserfs-list@namesys.com[/email], **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  [www.namesys.com/support.html](www.namesys.com/support.html). **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sdd
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
###########
reiserfsck --check started at Sun Sep 28 22:12:00 2008
###########
Replaying journal..
No transactions found
Checking internal tree..

Bad root block 0. (--rebuild-tree did not complete)

Aborted (core dumped)

---

### Post by fujikofujio on 2008-09-28
dmesg output when I tried to mount the drive

[12159.408846] ReiserFS: sdd: found reiserfs format "3.6" with standard journal
[12159.408901] ReiserFS: sdd: using ordered data mode
[12159.414282] ReiserFS: sdd: journal params: device sdd, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[12159.415307] ReiserFS: sdd: checking transaction log (sdd)
[12159.998070] ReiserFS: warning: is_tree_node: node level 47354 does not match to the expected one -1
[12159.998089] ReiserFS: sdd: warning: vs-5150: search_by_key: invalid format found in block 0. Fsck?
[12159.998100] ReiserFS: sdd: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1 2 0x0 SD]
[12159.998117] ReiserFS: sdd: Using r5 hash to sort names
[12159.998136] ReiserFS: sdd: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.
[12202.777292] ReiserFS: sdd: found reiserfs format "3.6" with standard journal
[12202.779625] ReiserFS: sdd: using ordered data mode
[12202.785827] ReiserFS: sdd: journal params: device sdd, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[12202.791682] ReiserFS: sdd: checking transaction log (sdd)
[12203.382859] ReiserFS: warning: is_tree_node: node level 47354 does not match to the expected one -1
[12203.382883] ReiserFS: sdd: warning: vs-5150: search_by_key: invalid format found in block 0. Fsck?
[12203.382895] ReiserFS: sdd: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1 2 0x0 SD]
[12203.382919] ReiserFS: sdd: Using r5 hash to sort names
[12203.392484] ReiserFS: sdd: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.

---

### Post by Pro-reason on 2008-09-28
If what you have tried doesn't work, then fixing the partition is probably impossible.  You need to [recover]("https://help.ubuntu.com/community/DataRecovery") what files you can, and then reformat that partition.  Hopefully you will be able to get back your most important stuff.  This is why you must always make [back-ups]("https://help.ubuntu.com/community/BackupYourSystem/TAR")!

Note that reiserfs is not the standard Ubuntu filesystem (ext3 is), so it's not entirely Ubuntu's fault.  That said, I have used reiserfs for years on my root partition, and I've never had any trouble.

---

### Post by fujikofujio on 2008-09-29
It's amazing, the best tool for recovering reiserfs is made for windows!

[http://www.ufsexplorer.com/](http://www.ufsexplorer.com/)

UFS Explorer just saved me, I was able to make an image of the failed drive, on my other pc with windows xp, I installed UFS Explorer. Then opened the image file that was shared on ubuntu over the network.

UFS Explorer scanned for the superblock and displayed all the folders I needed with the filenames intact and everything on that drive.

I was then able to right click on each of them and copy it to a spare drive on the windows pc. It was so easy I now regret wasting so much time on those command line tools where you have to read several man pages just to get started.

---

### Post by Pro-reason on 2008-09-29
I've just installed it via Wine.  

You should mention that that program is not free.  The trial version will only copy files under 64kB.  Are you sure you're not astroturfing?

---

### Post by fujikofujio on 2008-09-29
> **Pro-reason said:**
> I've just installed it via Wine.  

You should mention that that program is not free.  The trial version will only copy files under 64kB.  Are you sure you're not astroturfing?

No I am NOT astroturfing whatever that means, luckily I still got newsgroup access, but since I got comcast it won't be for long. I thought my days of pirating and pillaging were over... but after that HD crash had to go check my old newsgroups again and see if UFS explorer is available.

Lucky for me it was, I thought about running it in wine, but wanted to make sure it recovered my data instead of trying to play russian roulette with wine.

Don't get me wrong, I used to love ubuntu, even convinced one of my friend to switch to it. But lately I don't feel the love from ubuntu anymore...

---

