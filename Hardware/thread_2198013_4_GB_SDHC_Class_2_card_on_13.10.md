---
title: "4 GB SDHC Class 2 card on 13.10"
date: 2014-01-06
forum: Hardware
---

### Post by Marzian on 2014-01-06
Hello,
I&#8217;m using Ubuntu 13.10 (kernel 3.12) on a HP Sleekbook 15.

I&#8217;m not able to read any 4 GB SDHC Class 2 card (I have two, both SanDisk), while I can read a 8GB SDHC Class 10 card (Verbatim). 

The problem lies not in the cards, because they can be seen and accessed by the camera and Windows.

Already tried, to no avail:

- An external reader connected through USB (minicard reader or docking station)
- Two previous kernels: 3.11, 3.08
- KDE instead of Unity
- Another computer (Lenovo ThinkPad T400, but with the same OS)

In the previous edition of Ubuntu (13.04) the cards worked only if they were plugged-in at system start-up. Now, not even in that case.

Suggestions? 

Thanks for your time!

---

### Post by tfrue on 2014-01-06
Can you see them after you have plugged them in using ```
sudo fdisk -l
```

or when they are plugged in and typing ```
lsblk
```

---

### Post by Marzian on 2014-01-07
Yes:

```
sudo fdisk -l

Disk /dev/mmcblk0: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1            8192     7744511     3868160    b  W95 FAT32
```

```
lsblk
mmcblk0     179:0    0   3.7G  0 disk 
&#9492;&#9472;mmcblk0p1 179:1    0   3.7G  0 part
```

---

### Post by sudodus on 2014-01-07
You can try to mount it manually with the following command

```
sudo mount /dev/mmcblk0p1 /mnt
```

but I think it is partitioned in a strange way, which might be wiped, repartitioned and reformated with ***gparted***. But [COLOR=#ff0000]***save your data***[/COLOR] before doing that!

---

### Post by Marzian on 2014-01-07
The mounting worked, thanks!

Now, is there a way to make it automated, and to access the device so that I have the ownership as user, and not as root?

---

### Post by sudodus on 2014-01-07
You can use mount options in a command line that you save as a shell-script, alias or as a line in /etc/fstab. Read carefully about the mount options in

```
man mount
``` and ```
man fstab
```

Come back and ask if you need help to interpret those manuals :-)

-o-

But after partitioning with gparted, you might be able to automount it like any USB mass storage device (HDD, pendrive).

---

### Post by tfrue on 2014-01-07
Here is a fantastic site that explains how to use fstab. 
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Good luck,
tfrue

---

