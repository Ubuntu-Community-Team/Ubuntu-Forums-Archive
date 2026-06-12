---
title: "My Unpartitioned External Harddrive"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by AlwaysBored89 on 2007-08-14
Hi, I just bought an external hard drive case with the intent of putting a  spare hard drive I had into it so I would be able to store files I want on both my computers, and because I want to easily access, write, and change files from both the Ubuntu partition of my laptop and the windows partition. 

So, before I took the spare harddrive out of my desktop, I decided I needed to reformat it. (It had weird partitioning and a copy of XP on it) My desktop runs purely on XP, so I deleted all the partitions to make it just unallocated space and proceded to try to format it. I knew I needed to format it as Fat32 to make it easy for either operating system to play nice with it, however XP would only give me the option of reformatting as NTFS. So I decided I just needed to wait till I got the case and try to format it in Ubuntu.

The problem with this is, I can't see the harddrive now because it's all unallocated space. I'm not very familiar with Ubuntu, I've only had it a month. But does anyone know how I can locate it and thus format it as Fat32? Any help would be greatly appreciated :)

---

### Post by merlinus on 2007-08-14
ntfs is superior to fat anything, and ext3 is even better.  With the appropriate drivers, windows and ubuntu can read-write to either.

-merlin

---

### Post by matburton on 2007-08-14
I think you should be able to use gparted.
Hit ALT-F2 and type gksudo gparted and it may appear, if not then:
```

sudo apt-get install gparted

```
then do the above again.

I think you HD should show up and you can create a partition and format it as FAT32 in the GUI, be carefull though!
Back-up anything you hold dear first in case you have a moment of idiocy (happens to everyone ;-))

---

