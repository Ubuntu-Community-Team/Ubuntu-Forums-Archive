---
title: "Hard drive order?"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by Trebaruna on 2007-06-28
For the longest time I have had no problems with my hard drives (all SATA):
sda and sdb held various filesystems for operating systems (ntfs, ext3, xfs and swap) while sdc and sdd held data.

Yesterday I added a fifth drive to expand data storage, and after a bit of fiddling thought I'd got everything right.
It would now be sdc and the other data ones moved up one letter.

All was fine until I decided I wanted it to be NTFS instead of XFS for interoperability reasons. When I rebooted, however, the drive had suddenly started being sda, and what used to be a and b were now d and e.
If I format the drive back to XFS all is back to normal.

Still with me? The bottom line is: it would appear that the type of filesystem is affecting the order of drives. I don't want that, I just want the same order, regardless of whatever is on the drives.
Is there something I messed up? Is there a way to anchor the drive order?

Please note that due to the amount of drives, it is now set up such that the three data drives are on the nForce 4 SATA controller of my board (DFI Lanparty NF4 Expert), and the two linux (and windows...) drives are using the on board Sil3114 controller. Before the fifth drive all were on nForce.

Hopefully I've made the problem clear enough. I'll do my best to supply additional info where needed.

Thanks in advance!

---

### Post by renzokuken on 2007-06-28
i suppose its to do with which socket you plugged it into and whether its master or slave.

check the jumper on the back of the disk and make sure its set to "slave" position (should be a diagram on the drive itself, if not google for it)

---

### Post by Trebaruna on 2007-06-28
Thanks for your reply, but the drives are all SATA, there is no master/slave thing.

Also, the socket thing does have merit, but it would be unlikely: within the respective controllers I know the order in which drives will be listed, and they are, so that is working. What seems to be happening is that if I format the new drive one way it will put the nForce controller first on the list (thus those drives are sda sdb and sdc) and formatted the other way it is put second (so the other two drives are sda and sdb.

---

### Post by Trebaruna on 2007-06-28
I've now updated the fstab to only use UUIDs and that works, but it is inelegant: hard disks should just stay put!

So again: is there any way to hammer the order of hard disks in place?

---

### Post by unspellable on 2008-02-22
I am currently having a similar problem with a fresh Debian Etch installation.

In my case I have just installed Etch with 2 SATA and 6 SCSI drives. The 6 SCSI drives are in an external enclosure - that has its own power supply.

This makes for the following drive list:

/dev/sda
/dev/sdb
/dev/sdc
/dev/sdd
/dev/sde
/dev/sdf
/dev/sdg
/dev/sdh

I know the 6 SCSI drives were labeled sdc through sdh because of their size -> all 36GB while sda and sdb are both over 100GB each.

The basic partitioning is after this manor:
/boot /dev/sda1
/        /dev/sda5

'/' is actually on an LVM but the LVM isn't problematic because...

After I rebooted from the installation, the SATA and SCSI drives exchanged order such that the following (most important) changed places:

/dev/sda became /dev/sdg

So, while the installation process led me to believe there would be a certain order to the drives during normal operations the actual running system said other wise.

Thankfully I can turn off the SCSI enclosure's power, which restores normal order to /dev/sda... but this leaves those SCSIs unaccessible... and I found this post about using drive UUIDs - the which gives me some hope.


I will update with what success or failure I come across.

---

### Post by unspellable on 2008-02-22
Well, here I am. The UUID in the /etc/fstab worked.

Here was my original /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /boot           ext3    defaults        0       2
/dev/mapper/labanator-root_lab /               xfs     defaults        0       1
/dev/mapper/labanator-SWAP_lab none            swap    sw              0       0

/dev/sdb1       /home/vmware    xfs     defaults        0       2
/dev/mapper/scsis_lab-backups /home/backups   xfs     defaults        0       2

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

Here is my updated /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=8937c72c-1669-4e0e-9cdb-3102c8c25bae       /boot           ext3    defaults        0       2
/dev/mapper/labanator-root_lab /               xfs     defaults        0       1
/dev/mapper/labanator-SWAP_lab none            swap    sw              0       0

UUID=caa09c60-0eef-41e7-a800-6a28a080b6c2       /home/vmware    xfs     defaults        0       2
/dev/mapper/scsis_lab-backups /home/backups   xfs     defaults        0       2

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
```


I found out the UUIDs of the partitions via this command:

```
ls -l /dev/disk/by-uuid/
```

Which I in turn found at [linux.byexamples.com]("http://linux.byexamples.com/archives/321/fstab-with-uuid/")

---

### Post by twins on 2008-04-28
> **Trebaruna said:**
> Thanks for your reply, but the drives are all SATA, there is no master/slave thing.

Also, the socket thing does have merit, but it would be unlikely: within the respective controllers I know the order in which drives will be listed, and they are, so that is working. What seems to be happening is that if I format the new drive one way it will put the nForce controller first on the list (thus those drives are sda sdb and sdc) and formatted the other way it is put second (so the other two drives are sda and sdb.


Actually, I think the problem runs deeper. I have installed a SATA hardrive along with 3 IDE drives. I managed to put it working, and one day, out of the blue, Ubuntu changed the letters of the hardrives (I did absolutely nothing). I rewrote the fstab so that it would work again and someother day Ubuntu decided to change the letters again (again I did nothing to make it happen). So, maybe it's not the filesystem. There must be something else......

---

### Post by renzokuken on 2008-04-28
have you checked the device order in your BIOS? sometimes my BIOS changes the boot order of my drives and i have to reset them. i think its due to a nearly flat cmos battery, not sure.

---

### Post by vanadium on 2008-04-28
That is exactly the reason why UUIDs are being used nowadays. With current hardware, it cannot be guaranteed that a drive gets the same device name on each boot. In contrast, a partition can be uniquely and persistently identified by its UUID.

---

