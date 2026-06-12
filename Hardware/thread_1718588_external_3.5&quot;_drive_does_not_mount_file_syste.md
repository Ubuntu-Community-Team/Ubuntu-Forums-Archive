---
title: "external 3.5&quot; drive does not mount file system."
date: 2011-03-31
forum: Hardware
---

### Post by penduleum on 2011-03-31
I have the following problem.

A copple of mounts ago, i had 4 1 tb (3.5", sata) drives plugged in to my laptop via usb, and a power adaptor ( i just opened a external driver case and taked out the controler that was in there). All worked just fine, and i did whit all the drives, "safe remove", or shut down the drive whit disk util.

Now i have a wd external case, also 3.5", to use it whit my drives.
I did the same whit the other ( the other one was not my one, it was borrowed from a friend). Opened the case, taked out the drive (also 1 tb 3.5 sata) and pluged the mine. Then linked to the laptop, and put the plug in.

Disk util in linux reads the drive, but cant find the partition table.
I have checked all the 4 drives i have, and all have the same problem.

The wd caviar that was in the case, is working correctly.
I have also tryed all my other usb connections on my laptop, whit no success.

When i try manual to mount the drive whit this command: 
```
mount -t ext2 /dev/sdb /media/usb
``` i get this error:

```
root@laptop-....:/home/...# mount -t ext2 /dev/sdb /media/usb/
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@laptop-...:/home/...#  dmesg | tail 
[ 1391.826049] sd 11:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[ 1391.826056] sd 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1391.826067] end_request: I/O error, dev sdb, sector 0
[ 1830.844467] sd 11:0:0:0: [sdb] Unhandled sense code
[ 1830.844477] sd 11:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1830.844486] sd 11:0:0:0: [sdb] Sense Key : Data Protect [current] 
[ 1830.844497] sd 11:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[ 1830.844532] sd 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 02 00 00 02 00
[ 1830.844570] end_request: I/O error, dev sdb, sector 2
[ 1830.844966] EXT2-fs (sdb): error: unable to read superblock
```

Whit the other disks, i got diverent errors..
How can i still mount the drive so i can run fdisk on it, and safe the data?

thx all!!!


ps: whit webmin i can access some info of all the 4 drives, but cant mount them. Ony formating.. And that is somting i cant do (i have all my music collection on those drives. :( )

---

### Post by dabl on 2011-03-31
I cannot say for sure what the problem is, but here are a couple of notions:

- you wrote "ext2".  That's a very poor choice of filesystem type for such a large drive with important data on it.  ext4 would be the recommended filesystem type.

- you say you "safely removed", but, with ext2, I wonder whether we can be sure that the filesystems were not corrupted during removal or connection.

If this was my problem, I would do 2 things:

1. Make a Parted Magic Live CD or USB stick:  [http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

2. Find a desktop computer with SATA connectors that I could borrow, and connect each drive, one at a time, to SATA and power, and then boot the Parted Magic CD, and try to fsck the filesystem on the target hard drive.

If successful, I would back up my data, and then repartition those 1T hdds to ext4 filesystems, and then put them in the external USB enclosure.

---

### Post by penduleum on 2011-04-02
thx for the reply.

i agree whit the ext2 filesystem. but that was what i had chosen at that time... that is somting to change.

I already know what the problem is.
I have here a other disk, a 250 gb disk whit just plaine ntfs.
I know i can read that disk whit a other external disk controler (just the controler i had removed from the external case (also sata).


When i connect it using the wd controler, it gave me the same errors..
I suspect that the disks must be formated using the controler i whant to use, otherwise the partition table (whatever it is) whont be recogniged by the usb -> sata controler... at least this one i have.

i gona borrow one of my friend, that i know that worked, backup all the data and reformat it using the wd controler. And of course, i will use this opertunety to format it to ext4.

Its a strange problem, but i think i can resolve this by this workaround...

---

### Post by IcarusR on 2011-04-02
> When i connect it using the wd controler, it gave me the same errors..
Seems likely this controller could be failing.
> I suspect that the disks must be formated using the controler i whant to use,
It makes no difference what controller you use to format or use the drive with. If the controller works to format drive then drive should work with any working controller.

---

