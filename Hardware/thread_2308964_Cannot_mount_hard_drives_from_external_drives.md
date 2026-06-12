---
title: "Cannot mount hard drives from external drives"
date: 2016-01-06
forum: Hardware
---

### Post by swoncen2 on 2016-01-06
Hi,

I get the following error, while trying to mount a hard drive:

```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

This hard disk is a western digital green 4TB. It used to be an external drive but I removed the case and want to use it as an internal drive now.

fdisk -l:

```

Disk /dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xdb4bf07b

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1         256 976746239 976745984 465.8G 83 Linux

```

The strange thing is, that it only shows around 500 GByte for the first partition, but I used the whole space for this partition. I have data on this drive, so I cannot format it.

---

### Post by weatherman2 on 2016-01-06
Did you used to use this drive in Windows?

Fdisk shows "Disklabel type" as "DOS" (msdos) not "GPT" .  For a 4TB drive, you need to use GPT to see more than 2.1TB of space.   Otherwise, in Windows, you can use special software to make the drive usable without GPT, but this software as I understand it is not compatible with Linux.  Or, maybe there was something in the firmware of the external case you took it out of that was allowing it to be used with GPT that way.

---

### Post by swoncen2 on 2016-01-07
Hi weatherman,

I remember, that I used it only for my raspberry pi and the file system was ext4. However, it seems to be working now since I installed it in the external box again. All 4 TByte are detected for the first partition. I guess it would be safer for me to copy the content to other drives and then format it and copy back. At least for the very important data.

---

### Post by weatherman2 on 2016-01-07
Yes, that might be safer to copy it first.  Actually, please be careful NOT to have only *ONE* copy of your data on any device!  Hard drives fail all the time, sometimes without warning, and you could lose everything quickly if not backed up.  File system corruption, accidental deletion, and (if your data is ever accessible to a Windows system) malicious deletion could also put your data at risk.

---

### Post by swoncen2 on 2016-01-07
I know, I have 3 copies of important data on different devices. I still don't understand why I cannot mount the HD. However, If I want to format it later when installed in the PC, what do I have to do in order to have all of the 4TB accessible?

---

### Post by weatherman2 on 2016-01-07
Before you format it, delete the existing partition table and make a new one in GPT (not MSDOS) format.  In GPT format, you'll be able to make one large 4TB partition (if you like) or at least see the entire drive if you make smaller partitions.

I use the Gparted partition editor in Ubuntu to create/edit partitions.  The "Create Partition Table" option should be listed under the "Device" menu.  You can do it with command line commands too, if you prefer, but I find Gparted very easy to use.

---

### Post by swoncen2 on 2016-01-08
Ok, I found this: [http://dev-random.net/creating-mounting-partition-lager-2-tb-linux/](http://dev-random.net/creating-mounting-partition-lager-2-tb-linux/)
Thanks. Worked without a problem =)

---

### Post by weatherman2 on 2016-01-08
Even though I'm comfortable with the command line and use it for lots of things, for this type of thing I find doing it graphically with Gparted much easier, actually.  But, glad you got it figured out!

---

