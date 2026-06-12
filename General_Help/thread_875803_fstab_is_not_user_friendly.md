---
title: "fstab is not user friendly"
date: 2008-07-31
forum: General Help
---

### Post by hidarikani on 2008-07-31
I've added:
*a second optical drive
*a second HDD
Removed the floppy drive and resized some partitions

Now my fstab is all messed up and I have to edit it manually.
Wouldn't it be great to type something like 'update-fstab' in the terminal and it would be done automatically? fstab is generated during the installation, so the script already exists, right?

So do I really have to edit it manually?

---

### Post by iaculallad on 2008-07-31
> **hidarikani said:**
> I've added:
*a second optical drive
*a second HDD
Removed the floppy drive and resized some partitions

Now my fstab is all messed up and I have to edit it manually.
Wouldn't it be great to type something like 'update-fstab' in the terminal and it would be done automatically? fstab is generated during the installation, so the script already exists, right?

So do I really have to edit it manually?

Post whatever displays when you issue the following terminal commands below:

```
sudo fdisk -l
sudo blkid
```

and

```
cat /etc/fstab
```

So we could see what drive/partition are messed up.

---

### Post by hidarikani on 2008-07-31
sudo fdisk -l
```


Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b9a2b99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        3917    10490445   83  Linux
/dev/sda3            3918        8082    33455362+   f  W95 Ext'd (LBA)
/dev/sda4            8083        9964    15117165   83  Linux
/dev/sda5            3918        7833    31455238+   7  HPFS/NTFS
/dev/sda6            7834        8082     2000061   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000171c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux


```

sudo blkid
```


/dev/sda1: UUID="ECCC929DCC92619E" TYPE="ntfs" 
/dev/sda2: UUID="52231829-1ae8-4637-a699-1fa08d276b2b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="26117aac-507f-4e57-b0f2-b28aff8c073f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="408856F08856112" LABEL="Depository" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="ce0d54b7-b83c-46fe-adf7-ab052360c3ac" 
/dev/sdb1: UUID="5a407383-3e11-44cc-bd49-e12243a8a5ee" SEC_TYPE="ext2" TYPE="ext3" 


```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=26117aac-507f-4e57-b0f2-b28aff8c073f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=ECCC929DCC92619E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2 -- bad outdated line
# UUID=446863186863084E /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2 -- new updated line
UUID=52231829-1ae8-4637-a699-1fa08d276b2b /media/sda2     ext3    defaults 0       1
# /dev/sda5
UUID=0408856F08856112 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=ce0d54b7-b83c-46fe-adf7-ab052360c3ac none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#I no longer have a floppy
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
usbfs /proc/bus/usb usbfs auto 0 0

```

**Some questions:**
* I've commented the  floppy line and disabled the floppy in the BIOS but after entering in the terminal ```
sudo gparted
``` I get this:
```

======================
libparted : 1.7.1
======================
Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.
Unable to open /dev/fd0 - unrecognised disk label.

```
 and GParted is 'Scanning all devices' for like 10 minutes
* Now I have two optical drives, but only one of them is in the fstab maybe I should remove it because it should get mounted automatically?

By the way I've fixed the UUIDs for partitions on the old HDD but haven't mounted the new HDD (/dev/sdb) yet.

---

### Post by derrick81787 on 2008-07-31
First, I would make a backup copy of your current fstab:

```
sudo cp /etc/fstab /etc/fstab_backup
```

Adding the following to your fstab will mount the new drive on startup.  Replace <mount point> with the absolute path to the folder where you would like it to be mounted.

```
# /dev/sdb1
UUID=5a407383-3e11-44cc-bd49-e12243a8a5ee <mount point> ext3 defaults 0 1
```

As for your two cdroms, do you know the device names?  If one is /dev/hda (like you have in your fstab) and the other is /dev/hdb, these lines will work:

```
# cdrom
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

# other cdrom
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

Otherwise, just replace the names with the correct names.  They might be something like "/dev/cdrom0" and "/dev/cdrom1".  You could try putting disks in them and mounting them manually in order to figure out their names.

As far as the error message with the floppy goes, it might just be easier to uncomment the line in your fstab.  It shouldn't really hurt anything.  If there's no floppy drive present, then no floppy drive will get mounted.

Once you edit the file and save your changes, this command will cause the new changes to take effect, and it will give you an error message if there is something wrong:

```
sudo mount -a
```

Give that a try and let me know what happens.  If the command above gives any error messages, post them as well.

- Derrick

---

