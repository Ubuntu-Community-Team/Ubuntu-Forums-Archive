---
title: "Urgent: FSCK issue on startup"
date: 2008-09-11
forum: General Help
---

### Post by Titan8990 on 2008-09-11
When booting my server is dropping a root shell because it is halting here:

```
Log of fsck -C -R -A -a 
Thu Sep 11 15:36:12 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=1649f5ce-e869-4a3f-b7a9-e638e0bfdc80'
fsck died with exit status 8

Thu Sep 11 15:36:12 2008
----------------

```

That UUID is a external USB drive that is plugged in and functioning properly.

```
Disk /dev/sda: 250.0 GB, 250057219584 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3151

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29920   240332368+  83  Linux
/dev/sda2           29921       30401     3863632+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c310fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux
```

```
jordan@einstein:~$ sudo vol_id /dev/sdb1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=1649f5ce-e869-4a3f-b7a9-e638e0bfdc80
ID_FS_UUID_ENC=1649f5ce-e869-4a3f-b7a9-e638e0bfdc80
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
```

```
jordan@einstein:/var/log/fsck$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=567bbf65-3e84-4fc1-831e-74ee1603dd62 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
UUID=1649f5ce-e869-4a3f-b7a9-e638e0bfdc80       /media/backup   ext3    defaults        0       2
```


Anyone have any idea on why my boot up process is halting. It is key that my server can reboot without my intervention. 

I appreciate any help I can get.

---

### Post by bingoUV on 2008-09-11
Don't know why it is happening, but. In fstab, change the line for /media/backup to not fsck at boot. Just remember to fsck the partition manually from time to time. Change the line
```

UUID=1649f5ce-e869-4a3f-b7a9-e638e0bfdc80       /media/backup   ext3    defaults        0       2

```

to 
```

UUID=1649f5ce-e869-4a3f-b7a9-e638e0bfdc80       /media/backup   ext3    defaults        0       0

```

---

### Post by Titan8990 on 2008-09-11
Thank you, I had commented that line out completely as a temporary solution. That is much better than not having it automount.


I would still like to get some insight on why this is happening. Instabilities in a production server is not good.

---

### Post by vanadium on 2008-09-11
It might be that an USB drive is not yet operational at the time in the startup procedure that the file systems are mounted and checked. You might want to try disabling the line for the USB drive in /etc/fstab altogether: it probably will mount anyway, which is the default behaviour of USB drives.

Indeed, also in the latter case, the USB drive will not be checked. You could add a line to that purpose in /etc/rc.local, a script that is run the very last. Use the UUID specifier or label in that command, because nowadays device names are not guaranteed to be constant on each boot.

---

### Post by bingoUV on 2008-09-11
> **Titan8990 said:**
> Thank you, I had commented that line out completely as a temporary solution. That is much better than not having it automount.


Making the last column 0 would not stop the disk from automounting. It just stops Ubuntu from fscking it during boot.

Commenting the whole line means now you won't have total control over where the drive gets mounted. If the disk label is, suppose, 'data', it will get mounted at /media/data. But if there is another drive that is also labelled 'data' and gets mounted before your USB hard disk, the USB hard disk will get mounted at /media/data-1 or some such.

Where do you find your USB hard disk mounted after boot, now that you have commented the fstab line?

---

### Post by Titan8990 on 2008-09-12
> It might be that an USB drive is not yet operational at the time in the startup procedure that the file systems are mounted and checked. You might want to try disabling the line for the USB drive in /etc/fstab altogether: it probably will mount anyway, which is the default behaviour of USB drives.

That makes sense but I need to drive to mount to /media/backup


> Where do you find your USB hard disk mounted after boot, now that you have commented the fstab line? 

I have not rebooted the system since. This is currently a live production server. I'm in need of udev rules. I was unsure about the ones I had wrote and did not implement them. I bumped my thread for help on the udev rules every day for about 5 days with no luck.

The drive changes letters often. Today it is /dev/sdc1 next week it could be /dev/sdf1. Everyday when I come in I have to remount it and hope that it does not change before my backup script kicks in.

Again, thank you everyone for the help.

Edit: I also feel I should add that this drive was originally connected via eSATA. The drive would randomly not be detected by the BIOS causing the BIOS to hang. I found this to have something to do with my PCI RAID card. That is why I switched to USB where I otherwise would have never relied on a usb connection for backup.

---

### Post by vanadium on 2008-09-12
> That makes sense but I need to drive to mount to /media/backup

If you label the USB disk with "backup" it will automatically be mounted on /media/backup.

Anyway, another option that might work is to mount the USB disk with a mount command in /etc/rc.local.

---

