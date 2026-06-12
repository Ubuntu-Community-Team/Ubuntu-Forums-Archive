---
title: "SSD as boot drive"
date: 2012-11-14
forum: Hardware
---

### Post by BloodyDream on 2012-11-14
I tried to get some help on Linuxquestions.org but I couldn't. If I use an SSD as my boot drive only containing Ubuntu, the programs that come with it, and maybe a few others what size should I use? I'm building my own computer and I'm going to have 4 HDDs running RAID 10 and the SSD.

---

### Post by ahallubuntu on 2012-11-14
I have no idea what you will be doing with Ubuntu.  For me, 40GB would be plenty for the OS + swap.  Maybe you will be doing more, not sure?  40GB SSD drives (even 80GB) are not expensive anymore.

---

### Post by BloodyDream on 2012-11-14
Like I said, just a boot drive. I heard around 128-256 for windows but windows is huge compared to Ubuntu in terms of file size. I figured I'd go with 80.

---

### Post by ahallubuntu on 2012-11-14
I've done plenty of Ubuntu installations that fit just fine in 20GB.  Even XP will fit in 20GB - a bit tight.  Windows 7 needs more space, but I've had it running on a 60GB drive easily but without much installed.  80GB would be better for Windows 7.

So, I think 80GB will be more than enough for Ubuntu.  More than plenty unless you will be installing lots of stuff like building your own kernel, lots of software source code, etc.

---

### Post by oldfred on 2012-11-14
I have two full installs of Ubuntu in my 64GB SSD. I include /home but have all data including some of the hidden files & folders in data partitions on my rotating drives. I only have the FAT32 partition as I may move SSD to a new UEFI system and it will convert that to the efi partition. 

```
fred@fred-Precise:~$ sudo parted /dev/sdd unit s print
[sudo] password for fred: 
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name     Flags
 1      2048s      616447s     614400s    fat32                 boot
 2      616448s    618495s     2048s                            bios_grub
 3      618496s    58925055s   58306560s  ext4         Precise
 4      58925056s  117229743s  58304688s  ext4         Quantal

``````
fred@fred-Precise:~$ df -H
df: `/root/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        30G  9.2G   19G  33% /
udev            2.1G  4.1k  2.1G   1% /dev
tmpfs           830M  1.1M  829M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            2.1G  132k  2.1G   1% /run/shm
/dev/sdc2       107G   35G   73G  32% /mnt/shared
/dev/sdc6       104G   47G   52G  48% /mnt/data
/dev/sdd4        30G  4.7G   24G  17% /media/Quantal

```

---

### Post by BloodyDream on 2012-11-15
Thanks a bunch guys =) really helped a lot. I knew it couldn't be much, I mean Hell Ubuntu can boot from a USB it can damn sure boot from 80GB but I wanted to be sure. Semi-related, if anyone knows much about raid some help would be nice  it I have a few questions if you'd rather it be private.

---

### Post by oldfred on 2012-11-15
Best to start a separate thread in the server area. They know RAID a lot more.

---

### Post by BloodyDream on 2012-11-15
Will do. I checked out some SSDs earlier and a 128 is only a little more than an 80 price wise so I'm gonna go with that and maybe keep some important things on it.

---

### Post by ahallubuntu on 2012-11-15
You might start a new thread about RAID.  I did a software RAID once a few years ago with an old version of Ubuntu.  I got in trouble because I didn't know much about the Linux filesystem yet, and when I needed to run e2fsck, I kind of corrupted the array. :-(  Maybe things are better now, but you should probably be more careful than I was...

I don't use RAID anymore.  At best it protects you from hard drive failure but it can't protect you from file system corruption, accidental deletion, etc.  So you still need to make regular backups.  If you do those plus S.M.A.R.T monitoring, you are probably OK without RAID unless you have a mission-critical business or are just super paranoid about any potential data loss.

Unless you mean RAID to improve performance?

---

