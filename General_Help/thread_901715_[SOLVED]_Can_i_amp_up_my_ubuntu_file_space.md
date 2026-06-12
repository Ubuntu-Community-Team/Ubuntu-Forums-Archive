---
title: "[SOLVED] Can i amp up my ubuntu file space?"
date: 2008-08-26
forum: General Help
---

### Post by dragos240 on 2008-08-26
I set up 6 gb for my ubuntu portion, and now i've decided to max it out to 20gb. Any way i can change it?

---

### Post by tamoneya on 2008-08-26
yes there is.  The way you do it is you put in the install CD and boot from it.  You are not using it to reinstall but we need it because in order to change the partitions you cannot be running the OS from the partition.  Then you need to launch a program called gparted by going to terminal and typing:```
gksudo gparted
```

Then you can adjust the partition sizes.  Take note that partition resizing can be a very dangerous operation.  One small error can result in loosing all your data so make sure you have backups.  Also just so that we can help you out and maybe give you some recommendations can you show us the output of this command```
sudo fdisk -l
```
That will print your partition table so that if you have any questions we are a little more familiar with your system.

---

### Post by dragos240 on 2008-08-26
> **tamoneya said:**
> yes there is.  The way you do it is you put in the install CD and boot from it.  You are not using it to reinstall but we need it because in order to change the partitions you cannot be running the OS from the partition.  Then you need to launch a program called gparted by going to terminal and typing:```
gksudo gparted
```Then you can adjust the partition sizes.  Take note that partition resizing can be a very dangerous operation.  One small error can result in loosing all your data so make sure you have backups.  Also just so that we can help you out and maybe give you some recommendations can you show us the output of this command```
sudo fdisk -l
```That will print your partition table so that if you have any questions we are a little more familiar with your system.
I thought fdisk ment.... format disk. So wouldnt that completely destroy everything? And what would be the best method of backup.

---

### Post by tamoneya on 2008-08-26
fdisk can be used to format a disk but it is a general disk utility.  the -l option is "list".  Look it up in the help for man file if you dont believe me:```
fdisk --help
man fdisk
```

As for backing up I recommend just a USB harddrive although depending on how much data we are talking about I may change my recommendation.

---

### Post by dragos240 on 2008-08-27
> **tamoneya said:**
> fdisk can be used to format a disk but it is a general disk utility.  the -l option is "list".  Look it up in the help for man file if you dont believe me:```
fdisk --help
man fdisk
```As for backing up I recommend just a USB harddrive although depending on how much data we are talking about I may change my recommendation.
Yes i beleve you, but what do i do now. I did sudo fdisk -l and it did this:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c695658

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785       12161    91385752+   7  HPFS/NTFS
```
What command do i put in?

---

### Post by forger on 2008-08-27
He already said what to do :)
> The way you do it is you put in the install CD and boot from it.
Put in the Ubuntu live CD and boot using that CD, choose english and the live environment, then wait until it loads. After that you head to System > Administration > Partition editor

You select your hard drive using menu GParted > Devices, and then you resize it properly, by selecting a partition and clicking on "resize/move"

---

### Post by dragos240 on 2008-08-27
> **forger said:**
> He already said what to do :)

Put in the Ubuntu live CD and boot using that CD, choose english and the live environment, then wait until it loads. After that you head to System > Administration > Partition editor

You select your hard drive using menu GParted > Devices, and then you resize it properly, by selecting a partition and clicking on "resize/move"
Thanks. [strike]Solved[/strike]

---

### Post by dragos240 on 2008-08-27
I can't boot from CD. I tryed it and when i did. It stopped at "loading linux kernel". Then it never loaded >.<. Sorry for double posting. And i select "Try ubuntu without any changes to your computer". It just freezes right there, and never loads. If anyone can help me on this, please do.

---

### Post by meindian523 on 2008-08-27
CD error check?

---

### Post by forger on 2008-08-27
well you could:
1) check your downloaded iso with an md5
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2) check the cd for defects (in the boot cd menu)
3) try using a new(or lended) cd/dvd writer or a new cd :)

---

### Post by dragos240 on 2008-08-27
> **meindian523 said:**
> CD error check?
CD error check crashed. :(

---

### Post by jerome1232 on 2008-08-27
Also I just noticed fdisk -l didn't show any linux partitions... Did you by chance install using wubi?

---

### Post by dragos240 on 2008-08-27
> **jerome1232 said:**
> Also I just noticed fdisk -l didn't show any linux partitions... Did you by chance install using wubi?
Wubi? I installed ubuntu by going into winblows, i mean windows xp and using the autoplay option, and installing it into winbl- windows.

---

### Post by jerome1232 on 2008-08-27
Okay yup that would be what is known as wubi in which case all of this stuff we are saying, doesn't apply, wubi creates a virtual disk inside windows, I'd actually suggest reposting in the wubi section I have no idea how to expand the filesystem when you used wubi, it's a whole different ballgame.

---

### Post by dragos240 on 2008-08-27
> **jerome1232 said:**
> Okay yup that would be what is known as wubi in which case all of this stuff we are saying, doesn't apply, wubi creates a virtual disk inside windows, I'd actually suggest reposting in the wubi section I have no idea how to expand the filesystem when you used wubi, it's a whole different ballgame.
Oh i see. Thank you.

---

### Post by jerome1232 on 2008-08-27
Hey it's me again, I found this how-to hopefully it's of use to you [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

