---
title: "Using Testdisk to recover partitions?"
date: 2013-09-30
forum: Hardware
---

### Post by caiorrs on 2013-09-30
[FONT=times new roman][/FONT]Hey guys,

I`m facing a problem, I`m trying to recover my notebook's HD, a time ago it has stopped working and didnt recognize any of its partitions. So I bought a 1TB enternal HD to try to recover my partitions, at least my files, with testdisk, I searched out for many tutorials and step-by-step ways to recover my partitions, it founds my original partitions, but it says that the Structure is Bad, can you help me with it?

An image here:
[http://img809.imageshack.us/img809/7382/2ht7.png](http://img809.imageshack.us/img809/7382/2ht7.png)


Right now I'm using voyager 13.04 via live USB

Thansk, and sorry if I'm in the worng place, please move.

Yeah, I searched for it a lot!

---

### Post by oldfred on 2013-09-30
Did you change all those to P?
You can only have 4 primary and one of those primary has to be the extended to hold the logicals, or only three as P.
And you have overlapping partitions. You have to have one unique set of partitions with no overlap of start and ends. It shows old partitions so you will see both an old version and changed version. The more changes, the more old versions that may overlap will it show.

---

### Post by caiorrs on 2013-09-30
so, how can i repair it? or recover my files? I had a windows partition with 150GB a linux with 150GB (/ + /home) and the swap partition with 4GB and windows recover partition with 100MB

---

### Post by oldfred on 2013-09-30
You need to choose just those partitions where are after the changes. It also will show the before those changes. Swap is almost always logical, but your / and /home may or may not have been logical depending on how you installed.
Windows has to be primary and the recovery was probably an original primary partition. So one more primary at most and the rest had to be logical in the last extended partition. All logical partitions have to be adjacent to each other as you can only have one extended partition.

---

### Post by caiorrs on 2013-10-01
what do  I do after changing the partitions types?

---

### Post by oldfred on 2013-10-01
are you following these instructions?

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

After you create a valid partition table you have to write it.

---

### Post by caiorrs on 2013-10-04
Invalid partition structure.


??

---

### Post by oldfred on 2013-10-04
What did you select? Post screen.

---

### Post by caiorrs on 2013-10-04
All the screenshots here

[ATTACH=CONFIG]246743[/ATTACH][ATTACH=CONFIG]246744[/ATTACH][ATTACH=CONFIG]246745[/ATTACH][ATTACH=CONFIG]246746[/ATTACH][ATTACH=CONFIG]246747[/ATTACH]

---

### Post by caiorrs on 2013-10-04
[ATTACH=CONFIG]246748[/ATTACH][ATTACH=CONFIG]246749[/ATTACH][ATTACH=CONFIG]246750[/ATTACH][ATTACH=CONFIG]246751[/ATTACH][ATTACH=CONFIG]246752[/ATTACH]

---

### Post by caiorrs on 2013-10-04
I think my partitions are in lines 1,3,4 and 8 or 9, can you help me to configure them? I had Ubuntu in dual boot with windows 7. Ubuntu had 2 partitions / and /home and the swap, windows had only the recover partition (100MB) and the installation partition.

---

### Post by oldfred on 2013-10-04
8 would overlap so it must be 9. Then it is which are primary and which are logical.
1 & 3 have to be primary as that is normal Windows.
Swap is almost always logical and your Linux may be logical also.

You are showing only one Linux partition unless you overwrote Windows which then is a separate issue and may not be recoverable.

---

### Post by caiorrs on 2013-10-04
maybe I did just the /, I can't remember very well =S, But what are all the types? Like * P D E L ? sorry, but I have knowledge about this, but never did it before, and I'm very careful when I'm working with data. Sorry

---

### Post by oldfred on 2013-10-04
I have never reset partitions from testdisk.
But instructions say P is primary and L is logical. Your first partition should be the bootable one or *.

---

### Post by caiorrs on 2013-10-04
yeah, but i have 2 bootable partitions, windows an ubuntu... i'll try just windows *, but ubuntu would be what type? and the 100MB windows partition?

---

### Post by caiorrs on 2013-10-04
I can list my files to backup them!!, but I'm still wanting to recover the partitions

---

### Post by oldfred on 2013-10-04
The 100MB is the first partition and that is the Windows boot partition normally. 

Grub does not use boot flag, that is a Windows convention, so boot flag is not required on Linux partitions (unless booting with Lilo). And only one partition per drive can have boot flag. With Windows it must be a primary partition.

---

### Post by caiorrs on 2013-10-11
thanks man, now I can read all my files, but I'm still have problems with windows. I'm very thankful to you, really, thankssss =D. One more information, some files that I could not read (from windows partition), were able to read after I run chkdsk /f /r, it rebuilt the paths and I could read all my files. Just one more question. Is there any equivalent command to restore the linux paths? Because there's still some files that I cant read from ubuntu =S

Again, THANK YOU!!

---

### Post by oldfred on 2013-10-11
This is for ext family of Linux formatted partitions.

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by caiorrs on 2013-10-11
I ran fsck becaus I could not use you tip.
here it is

sudo fsck /dev/sda3
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda3 contains a file system with errors, check forced.
Resize inode not valid.  Recreate<y>? 


recreate?

---

### Post by oldfred on 2013-10-11
I have not seen that error but I would think you have to recreate.

---

