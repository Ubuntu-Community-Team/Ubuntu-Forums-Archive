---
title: "Unable to write to second drive"
date: 2008-05-07
forum: Hardware
---

### Post by lloydlloyd on 2008-05-07
Hey, I'm running 8.04 and have had a second harddrive in the machine. my first is just a small 40gb, and the second is 200gb where i want to store most my data (music movies photos etc). except i can't write anything to the drive. i've tried playing around with gparted as i've found in some other threads, but i can't figure out how to  enable write privileges for all users. any help would be great.

thanks
lloyd....

---

### Post by unutbu on 2008-05-07
Please post the output of

```
sudo fdisk -l
mount
ls -ld <mount point>
```

where <mount point> is the directory corresponding to the second drive.

---

### Post by VMC on 2008-05-07
> **lloydlloyd said:**
> Hey, I'm running 8.04 and have had a second harddrive in the machine. my first is just a small 40gb, and the second is 200gb where i want to store most my data (music movies photos etc). except i can't write anything to the drive. i've tried playing around with gparted as i've found in some other threads, but i can't figure out how to  enable write privileges for all users. any help would be great.

thanks
lloyd....If you run command 'sudo fdisk -l' does the second drive show up?


Are both drives IDE or SATA, and is the second drive NTFS partition or is their _any_ partition on it?

---

### Post by lloydlloyd on 2008-05-07
> **unutbu said:**
> Please post the output of

```
sudo fdisk -l
mount
ls -ld <mount point>
```

where <mount point> is the directory corresponding to the second drive.
Here is what I got:

> Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35353535

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4675    37551906   83  Linux
/dev/sda2            4676        4863     1510110    5  Extended
/dev/sda5            4676        4863     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31022912

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux


---

### Post by lloydlloyd on 2008-05-07
> **VMC said:**
> If you run command 'sudo fdisk -l' does the second drive show up?


Are both drives IDE or SATA, and is the second drive NTFS partition or is their _any_ partition on it?

the "'sudo fdisk -l" command results are in my previous post.

I had previously had an ntfs partition on the drive (from when i was running windows) and i had music etc already on there. just when i loaded ubuntu on, i was unable to write to that drive anymore. i have backed everything up and have tried formatting it to the ext3 file system using gparted.
Oh and both drives are IDE

---

### Post by VMC on 2008-05-13
> **lloydlloyd said:**
> I had previously had an ntfs partition on the drive (from when i was running windows) and i had music etc already on there. just when i loaded ubuntu on, i was unable to write to that drive anymore. i have backed everything up and have tried formatting it to the ext3 file system using gparted.
Oh and both drives are IDE
Since you reformated the second hard drive to ext3, can you now write to it?

Aslo, hardware wise, how are the configured? Is the second HD a slave off the first, or are you running both off their own controller?

Does 'mount' command show the second drive. Anything in /mnt , /media, cecides cdrom?

---

### Post by lloydlloyd on 2008-05-13
> **VMC said:**
> Since you reformated the second hard drive to ext3, can you now write to it?

Aslo, hardware wise, how are the configured? Is the second HD a slave off the first, or are you running both off their own controller?

Does 'mount' command show the second drive. Anything in /mnt , /media, cecides cdrom?

I did a google search for mounting a drive in linux, and i have managed to get the drive writable by editing some file I now forget. only trouble is now the drive doesn't mount when i restart the computer. so any ideas or anything further you need?

thanks for the help by the way

---

### Post by unutbu on 2008-05-13
Try
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

