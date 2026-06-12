---
title: "Formatting disk drives without Gparted"
date: 2008-12-17
forum: Hardware
---

### Post by Rahzizzle on 2008-12-17
OK so, I ran out of space on my partition but I installed Ubuntu Server Edition on another partition (or so I thought) and there is 94GB of free space that I want to format because I never use the server edition.

I go into GParted and this is what it shows
[IMG]http://i3.photobucket.com/albums/y68/rahzizzle/Gparted.png[/IMG]

Now, I don't get it because I have a windows partition also installed so there are definitely 3 partitions plus a swap but it is not picking any of them up. 
Here's a picture of my filesystem where it says no space
[IMG]http://i3.photobucket.com/albums/y68/rahzizzle/filesystem.png[/IMG]


and this is the Server Edition partition which for some reason is located under /media/disk
[IMG]http://i3.photobucket.com/albums/y68/rahzizzle/serveredition.png[/IMG]

So my question is how exactly do I format that 94GB drive and tap into it so I have more disk space??!
:???:

---

### Post by xXJT-JaredXx on 2008-12-17
maybe try another program? Qpart or something . .i had something similar happen where i was trying to get more space by changing partitions and it started to screw up and ended up loosing half of it and needed to completely wipe it and start again. so maybe try using something different to edit partitions and try again.

---

### Post by taurus on 2008-12-17
What's the output of this command from a terminal?

```
sudo fdisk -l
```
And by the way, run gparted with root privilege.

```
gksudo gparted
```

---

### Post by Rahzizzle on 2008-12-17
sudo fdisk -l output:
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5424a154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8149    65456811   83  Linux
/dev/sda2   *        8150       17264    73216237+   7  HPFS/NTFS
/dev/sda3           17265       30401   105522952+   5  Extended
/dev/sda4           29269       30401     9100791   82  Linux swap / Solaris
/dev/sda5           17265       28774    92454012   83  Linux
/dev/sda6           28775       29268     3968023+  82  Linux swap / Solaris

Also, I did use Alt + F2 and typed gksudo gparted but thanks for the tip anyways! :guitar:

---

### Post by logos34 on 2008-12-17
here's the partition you want to delete:

> **Rahzizzle said:**
> 
**/dev/sda5           17265       28774    92454012   83  Linux**


You can use fdisk from the CLI.  It's all explained here:

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

Hopefully, in the process of deleting and creating new partition it will fix the partition table so gparted can read it.

also, get rid of the other (server) swap partition.  you only need one

---

### Post by Joe2Shoe on 2008-12-17
I personally would download the latest GParted v.0.4.1 and burn it to a CD and reboot the pc and repartition the drive.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754)

That procedure always works for me, flawlessly.
Good luck,
Joe2Shoe.

---

### Post by Joe2Shoe on 2008-12-17
Don't use the previous link, that's the unstable version v0.4.1.

Here's the Live CD v0.3.9-13 in .iso format.

Just download the .iso file and burn the image to a CD.
Then reboot pc with CD in CD/DVD drive and repartition drive as needed.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by Rahzizzle on 2008-12-18
Thanks a bunch! and using this method won't erase the data I already have on the first partition?

---

### Post by Joe2Shoe on 2008-12-18
If you want to keep the data on the first partition, leave it alone!
Just partition/format the other partition(s).
You can resize a partition by left-clicking it, then clicking resize, creating 2 smaller partitions.
Just don't touch the first partition, if that's important data or the OS!
If the first partition has too much free space, you can resize it, creating 2 smaller partitions.  Just don't delete the data, and give the first partition some free space.

I use GParted on Linux and Windows hard drives.
I use EASEUS's Partition Manager in Windows, also (freeware).
[http://www.easeus.com](http://www.easeus.com)
Good luck.

---

