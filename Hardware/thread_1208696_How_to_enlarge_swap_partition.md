---
title: "How to enlarge swap partition?"
date: 2009-07-09
forum: Hardware
---

### Post by larry on 2009-07-09
Dear All,
My laptop seems rather slow to me when doing number crunching.
If I look at
$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    7992    0    -1 

Does that mean that I have about 8Gb of space in my swap partition or have I chosen by mistake to create an 8Mb partition?
If the latter, how can I enlarge the swap partition to reach about 8Gb?
Many thanks

larry

---

### Post by anystupidname on 2009-07-09
What about:
free -m
and
cat /proc/meminfo
to see how much is in use...
Or you could just run gnome-system-monitor I suppose...

---

### Post by raymondh on 2009-07-09
> **larry said:**
> Dear All,
My laptop seems rather slow to me when doing number crunching.
If I look at
$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    7992    0    -1 

Does that mean that I have about 8Gb of space in my swap partition or have I chosen by mistake to create an 8Mb partition?
If the latter, how can I enlarge the swap partition to reach about 8Gb?
Many thanks

larry

Hi Larry,

I think you created 8MB.  Here is my swapon -s on the test machine

 Filename				Type		Size	Used	Priority
/dev/sda7                               partition	5957240	0	-1
 
I did 6GB for swap.

Good luck.

---

### Post by anystupidname on 2009-07-09
If you have free space on your drive, you can just swapoff and make the partition larger with gparted or fdisk. If not, you can use [unetbootin' partedmagic]("http://sourceforge.net/projects/lubi/files/PartedMagic%20Partition%20Manager/unetbootin_partitionmanagerrev146_all.deb/download")

---

### Post by larry on 2009-07-09
> **anystupidname said:**
> If you have free space on your drive, you can just swapoff and make the partition larger with gparted or fdisk. If not, you can use [unetbootin' partedmagic]("http://sourceforge.net/projects/lubi/files/PartedMagic%20Partition%20Manager/unetbootin_partitionmanagerrev146_all.deb/download")

You see, I tried your suggestion , but I cannot resize \home since I am told that the partition has an incompatible feature (is it the fact that it is encrypted?). Otherwise, I  would be happy with a swap file.
I saw
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) , 
but the problem is that I would like to create the (large) swap file inside /home (in order not to run short of space in /root), but the procedure does not work outside the root filesystem: I am always told that the generated swap file has holes.
I am a bit confused at this point.
Cheers

larry

---

### Post by anystupidname on 2009-07-10
Holes?!? I'm not following you....

First off, swap must be a raw partition of its own. PartedMagic has a "swap" file system option available when you create a new partition in a free space area.

Second, unless your system has more than 8GB of RAM, there isn't a reason to have such a large swap partition. I believe the rule of thumb is a swap partition 1 to 1.5 the size of your RAM depending on how much RAM that is...

Third, I don't know if not being able to resize an encrypted file system/partition is a limitation of PartedMagic or not. (I would guess not but it would depend on what type of encryption system..) So you should be able to reduce the size of /home or / or both as necessary to create enough free space for the swap partition that you want.

Finally though, there is generally little to no advantage to using a swap partition on systems with large amounts of RAM except in unusual roles. (VMware server for example)

---

### Post by larry on 2009-07-10
> **anystupidname said:**
> Holes?!? I'm not following you....

First off, swap must be a raw partition of its own. PartedMagic has a "swap" file system option available when you create a new partition in a free space area.

Second, unless your system has more than 8GB of RAM, there isn't a reason to have such a large swap partition. I believe the rule of thumb is a swap partition 1 to 1.5 the size of your RAM depending on how much RAM that is...

Third, I don't know if not being able to resize an encrypted file system/partition is a limitation of PartedMagic or not. (I would guess not but it would depend on what type of encryption system..) So you should be able to reduce the size of /home or / or both as necessary to create enough free space for the swap partition that you want.

Finally though, there is generally little to no advantage to using a swap partition on systems with large amounts of RAM except in unusual roles. (VMware server for example)

See the link for the fact that you have to be careful when creating the swap file (not any file will do). There they mention holes.
Fundamentally, my problem is that partedmagic or parted itself seem to have a problem with encrypted partitions. 
Any idea here? has anyone installed Ubuntu (via minimal CD in my case), encrypted the /home and been able to resize it without a live CD?
This is what I would like to know.
Cheers

larry

---

