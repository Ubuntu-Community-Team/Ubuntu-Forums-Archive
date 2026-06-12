---
title: "Ubuntu partition not readable from Windows."
date: 2009-11-19
forum: Hardware
---

### Post by McMichael96 on 2009-11-19
On Windows's disk management program it show the partition but it want let me open it. It wont show it on "Computer" (used to be My Computer in XP). Please help my pictures and music or on the partition but i want them readable from Ubuntu AND Windows.

---

### Post by teward on 2009-11-19
Ubuntu partitons are NOT, I repeat, NOT readable on Windows.  It just isn't possible.

---

### Post by sjosul on 2009-11-19
You could set up a separate partition formatted in FAT32 or NTFS for shared files, which would be accessible in both.

Alternatively, if your Ubuntu partition is Ext 3 there are several options, here:

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I've used Ext2IFS successfully in Windows XP and Windows 7 to access an Ext 3 partition.

---

### Post by coffeecat on 2009-11-19
> **TrekCaptainUSA said:**
> Ubuntu partitons are NOT, I repeat, NOT readable on Windows.  It just isn't possible.

It's always best not to make dogmatic statements. The post following yours might just prove you wrong. :wink:

> **sjosul said:**
> Alternatively, if your Ubuntu partition is Ext 3 there are several options, here:

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I've used Ext2IFS successfully in Windows XP and Windows 7 to access an Ext 3 partition.

There is one problem with the Ext2 IFS driver. From your second link:

> [SIZE=2]**[SIZE=3]Large inodes [/SIZE]**   
         [/SIZE]                              The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.             
              Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them. 
              Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup.Inodes of 256 bytes have been default in ext3 partitions created by Ubuntu since Intrepid iirc. Possibly Hardy. And true of practically every other distro for the last 12-18 months. It's curious that the Ext2IFS driver developer hasn't addressed this issue. And I don't know whether this also affects the other drivers mentioned in your first link, but that link is from 2007.

All-in-all, it's probably better for the OP to make a shared NTFS or FAT32 partition as you suggest. I was always nervous of accessing an ext3 partition from Windows when I did it a couple of years ago.

---

### Post by matrik22 on 2009-11-19
>  It's always best not to make dogmatic statements. The post following yours might just prove you wrong. :wink:

Indeed.

---

### Post by seeker5528 on 2009-11-19
The short answer.

My preference for things I want to have available in Linux and Windows both is to have a separate data partition that is formatted NTFS.

The slightly extended answer.

Even for the stuff I only want to have available in Linux I keep separate partitions for data and to keep a spare copy of email and bookmarks and things, so I can reformat and re-install without having to worry about losing a bunch of stuff and in my case also so I don't have to worry about what kind of screwy things are going to be caused by attempting to use a single home directory for multiple distributions.

Later, Seeker

---

