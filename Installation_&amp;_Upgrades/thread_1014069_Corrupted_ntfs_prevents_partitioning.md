---
title: "Corrupted ntfs prevents partitioning"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by night_fox on 2008-12-17
Hi, I have used Ubuntu for ages on my laptop and I am trying to install it on a fairly old PC at home for my family to use. I can boot Ubuntu 8.10 Intrepid Ibex from the live cd. The live cd won't resize my partition, and the gparted Partition Editor wont either. Instead it tells me to run

```
ntfsclone --rescue
```

then to go to windows and use

```
chkdsk /f /r c:
```

Then to go to back to Ubuntu and do

```
ntfsresize --bad-sectors
```

before creating the partitions for Ubuntu.

The ntfs partition size is 80 gigabytes. I did the first one and started cloning the filesystem to my external hard drive. I left it for 6 hours and it had done 12%, so it might have taken 50 hours to complete the whole thing. My mum thinks that a computer left on overnight is a fire hazard, also, that sort of time is impractical. Is there a better way of doing it?

Also, does ext3 look for and work around bad sectors when it gets installed?

---

### Post by night_fox on 2008-12-19
bump. Please can I have some advice?

---

### Post by Mark Phelps on 2008-12-19
I'm probably going to get flamed big-time for saying this, because I've dared to criticize an Linux utility (GParted), but it's been MY experience that it doesn't handle NTFS partitions well.  Windows-based partition managers (not surpisingly) do a lot better job of handling NTFS partitions -- but you have to pay for those.

What MIGHT work is the following:
1) Boot from a current (8.10) live cd
2) Open Synaptec and see if ntfs-3g is installed (I'm guessing it is), If not, install it
3) Check if ntfs-config is installed (probably not), and install it
4) Run ntfs-config from the Applications menu
5) Select the NTFS partition and allow it write access
6) Open GParted (if not in the System --> Administration menu, you'll have to install it in Synaptec)
7) See if it will NOW allow you to mess with the NTFS partition.
8) If it does, you're OK; if it doesn't, don't know what else to do apart from getting a Windows-based paritioning tool.

---

### Post by clw3388 on 2008-12-19
If box is old and you are installing linux.. why resize the ntfs? Kill it by letting the install format it..

---

### Post by night_fox on 2008-12-19
Thankyou Mark. I will certainly try that. I'll post here again when I have!

I will never pay for a partition editor, so if it doesn't work, the only thing to do would be ve......ry long. Supposing my HD is covered in bad sectors, why could I not just recursively copy all the data onto another HD formatted to ntfs?

---

### Post by night_fox on 2008-12-21
OK, I tried that and it didn't work. However, I copied each and every file on the ntfs partition to my external hard drive and it took 2 hours.

I dont know what could be wrong with doing this. I got every file, and to prove it,:
```
ls -Rl /media/disk >> lsdisk
ls -Rl /media/FreeAgent\ Drive/backup >> lsbackup
diff lsdisk lsbackup
```
no output so every file must be backed up.

To resize the internal ntfs:
```
ntfsresize --bad-sectors -s 55G /dev/sda2
```

I copied the output of several partition manipulators and used dd to make a backup of the mbr and then used cfdisk to change the partition table.

Then I installed Ubuntu

Ubuntu is awesome, but I dunno how any non-geek would be able to install Ubuntu if they had to do that.

---

