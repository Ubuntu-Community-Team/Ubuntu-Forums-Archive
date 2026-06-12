---
title: "Need advice on migrating to new disk"
date: 2010-04-11
forum: Hardware
---

### Post by /carlito on 2010-04-11
Hey,

I would like to have some feedback on this migration that I am planning. A little background on my current setup first:

I have 3 disks in my system which provide me with 1T of data storage. 2 of the disks are setup as an nvidia RAID-0 and all of them are running in a LVM to create an XFS media storage partition. Unfortunately one of the RAID disks is failing on me and I will migrate to a different setup as this is setup is to error prone imo. My root fs is running from an old IDE disk and this also needs to go on the new drives so I am left with only 2 drives in my system. Mother nature will thank me :)  

Realizing that I need to expand my storage I decided to buy a WD 1.5T caviar green. This would allow me to get rid of the 2 x 250G seagate drives which are currently in the RAID. (remind me never to buy seagate again...) To have some redundancy in this setup I will be using my trusty 500G WD to create a SW RAID-1. Naturally I would like to prepare my system for future storage upgrades so I will combine this with LVM.

Thinking about how to design this system led me to come up with [_**this_**](http://dl.dropbox.com/u/929121/clio_new_partition_setup.png) setup. Basically I will create 2 linux RAID-1 devices, 1 for / and 1 for redundant data storage. The last will be using LVM on top of the RAID for flexibility and future expansions. Finally I will use the rest of the 1.5T disk for media storage. This will also be running on top of LVM.

The only problem is that I currently don't have any storage to backup all my media files while I do the migration so I came up with following steps to migrate from the old situation to the new one.


[list]* Fdisk new 1.5T drive with 4 partitions
* Setup swap
* Create LVM media/mythtv and make XFS 
* Cp -Rvp /mythtv media/mythtv
* Verify media/mythtv data by mounting to /mythtv and running like this for 5 days
* Remove old LVM and blank 500G disk
* Shutdown and remove unused disks + plug new disks in SATA1 + 2
* Boot into live cd
* Setup md0 and 1
* Create ext4 for md0
* Create LVM mirror/redundant and make XFS
* Cp -Rvp / /dev/md0
* Configure /etc/fstab
* Setup GRUB on hd0 and hd1
* Shutdown and remove IDE disk
* boot into new setup and live long and prosper[/list]


I think this should cover the migration but would like to make sure that I am not missing anything as this is still a risky operation... I know that it would make the process a LOT easier if I just had some kink of external storage where I could "park" the files while migrating to the new setup, unfortunately this is not an option at the moment.

Please feed me with your comments/insults/suggestions/improvements!!!

Cheers.

---

### Post by mulperi on 2010-04-11
When you fdisk the WD EARS 1,5TB Green Caviar, be sure to google about the 4k alignment issue. At least mine is not aligned and I am getting very bad write speeds. Trying to fix this after initial fdisk operations is pain.

---

### Post by /carlito on 2010-04-11
> **mulperi said:**
> When you fdisk the WD EARS 1,5TB Green Caviar, be sure to google about the 4k alignment issue

Tnx a lot for this tip. I was unaware of the issue so I would definitely have suffered from bad performance on my drive! As a reference for other users use fdisk with these parameters ensures that every partition you create is aligned to 4KiB boundries.  

```
fdisk -H 224 -S 56 /dev/sdx
``` 

[_**source_**](http://community.wdc.com/t5/Desktop/Problem-with-WD-Advanced-Format-drive-in-LINUX-WD15EARS/td-p/6395)


[edit] [**_Here](http://anandtech.com/show/2888)**_ you can find a nice explanation of the whole 4k allignment issue and why it was implemented in the first place! [/edit]

---

### Post by /carlito on 2010-04-11
I also posted this on the gentoo forums. You can go [**_here](http://forums.gentoo.org/viewtopic-t-823028.html[/url)**_ to follow the thread.

---

