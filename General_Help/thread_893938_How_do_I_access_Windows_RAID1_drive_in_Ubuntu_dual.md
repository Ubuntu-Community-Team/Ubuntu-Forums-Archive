---
title: "How do I access Windows RAID1 drive in Ubuntu dual boot?"
date: 2008-08-18
forum: General Help
---

### Post by jrdecastro on 2008-08-18
System has 3 hard drives, one with Ubuntu 8.04 in a single drive (non-RAID) and a RAID1 array of two drives containing Windows.
/sdc is a 350GB hard drive containing the entire Ubuntu installation, formatted ext3
/sda and /sdb are 500GB each and configured as a RAID1 array, fomratted NTFS, and hold Windows XP32 and XP64 in three partitions:
C: is 120GB and holds Windows XP32
D: is 200GB and holds user data
X: is 80GB and holds Windows XP64
The RAID1 configuration of the Windows disks predates the Ubuntu installation and is Intel native motherboard RAID - motherboard is Intel DP35DP so in Ubuntu-speak it's "fakeraid".
Booting is triple boot - XP32, XP64, and Grub, which in turn loads Ubuntu 8.04.
 dmraid is installed and shows the RAID1 arrays
dmraid -ay shows :
sudo dmraid -ay
RAID set "isw_ebcfidajef_Volume0" already active
RAID set "isw_ebcfidajef_Volume01" already active
RAID set "isw_ebcfidajef_Volume05" already active
RAID set "isw_ebcfidajef_Volume06" already active

where isw .....Volume0 is the entire 500GB disk, 01 is the XP32 partition, 05 is the data partition, and 06 is the XP64 one.
When I look in Nautilus I see "Filessytem" which contains the Ubuntu files, and six other drives - two for XP32, two for data, and two for XP64, but I don't see the three RAID1 entries, so I suspect that if I write to any of the six partitions it will likely not get mirrored to the other one it is paired to...
How do I change this so my file system shows the Ubuntu file system and just 3 RAID1 entries somewhere for the 3 Windows RAID1 partitions? I would (perhaps naively) expect instead to see /dev/md0, md1, and md2 or something similar

Also, fstab does not list the RAID partitions :
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdc1
UUID=40fa1aac-1681-4690-9b3b-6209d795da71 / ext3 relatime,errors=remount-ro 0 1
# /dev/sdc5
UUID=ccc25a40-e40e-41cc-a37a-d24a1b6c6135 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdd /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

so somehow they are not being recognized?

Help please!

---

### Post by fjgaude on 2008-08-19
I haven't used **dmraid** for years but remembering, this might point you in the right direction. You need to put into the fstab file the devices that are to load.

A line would look something like this:

```
/dev/mapper/isw_ebcfidajef_Volume0 /dev/mountpoint ntfs defaults 0 0
```

And do this for each device. Of course you have to make the mountpoints first:

```
sudo mkdir /media/vol0
```

Or something like that.

Let us know how you are doing.

---

### Post by jrdecastro on 2008-08-23
Thanks a lot - that worked beautifully!:)
I created 3 directories - XP32C, XP32Data, and XP64 and mounted them in fstab.
They now appear as little icons on the desktop and can be accessed like any other drives.

One problem that has now come up is permissions - it seems to set none.
If I right click on the mounted XP drive and select "properties", then "permissions" it says "the permissions of  "XP32C" could not be determined", and if I create a "guest" account with very low privileges in my system and log on as the unprivileged guest, the three XP dirves are still on the desktop and the guest can still mess with them. How do I protect them so that only my account (or administrative users) can touch them?

---

### Post by fjgaude on 2008-08-23
Gosh, I'm not sure... maybe this is something beyond...

The issue is that NTFS is different to the Linux ext3 when it comes to permissions... I think you would have to somehow declare permissions to the NTFS partitions and files while you are in Windows. I really have no experience with these kind of things.

Think about mount point, being secure with high permissions?

Maybe someone here has an idea.

---

### Post by Cholsen on 2008-10-03
The mount options are listed here:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting%20Fakeraid]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting%20Fakeraid")

So I mounted my Windows RAID1 partitions for testing purposes read-only using this line in fstab:
```
/dev/mapper/pdc_digjcfieg1       /media/winc   ntfs   ro,user,auto,fmask=0177,dmask=0077,uid=1000 0       0
```

But my individual partitions the RAID1 consists of are still listed in the GNOME file browser, in addition to the combined one. So I have "C", another "C", and the merged "winc". How do I let the first two disappear?

---

### Post by fjgaude on 2008-10-03
I have no idea... it's not a perfect world, yet. <smile>

---

