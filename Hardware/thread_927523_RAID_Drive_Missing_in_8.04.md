---
title: "RAID Drive Missing in 8.04"
date: 2008-09-23
forum: Hardware
---

### Post by Speedy162005 on 2008-09-23
So my secondary hard drive set seems to have disappeared. I think it's linked to the fact that I had to hard shut down my computer after it failed to sleep.

Anyways, here is my situation. 6 hard drives in this computer, the main one is 80GB, this works just fine. The External USB works just fine as well.

I have 4 300 GB Seagate drives setup in 2 RAID1 arrays. 

It detects one set, but not the other. Any help would be greatly appreciated. I'm using Ubuntu 8.04 64Bit


sudo fdisk -l

```


Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5be15be1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5be15be1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/md0: 300.0 GB, 300066267136 bytes
2 heads, 4 sectors/track, 73258366 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008c7e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        9327    74919096   83  Linux
/dev/sde2            9328        9729     3229065    5  Extended
/dev/sde5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35c5d30d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001    7  HPFS/NTFS


```

cat /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d2daa50e-4eba-46dd-8e9a-15a3594943e5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=717e6ff5-913d-423b-8cf5-1c288677516b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/md0	/mnt/drive_e	ext3	rw,user,auto,exec,	0	0
/dev/md1	/mnt/drive_f	ext3	rw,user,auto,exec,	0	0

# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```


Thanks! ~T.

---

### Post by Speedy162005 on 2008-09-23
Still messing around with it, I haven't quite figured out what's wrong with it yet.

---

### Post by Speedy162005 on 2008-09-29
So as it turns out, my /md1 is missing.

Gparted shows the 2 drives as both having RAID on them, but it's missing /md1, md0 shows just fine.

I tried dismantling /md1 from the system and rebuilding it as /md3 but that told me the device was busy or in use.

---

