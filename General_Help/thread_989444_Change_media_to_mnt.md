---
title: "Change /media to /mnt"
date: 2008-11-21
forum: General Help
---

### Post by ktechman on 2008-11-21
I recently upgraded to 8.10 from 8.04 and after 3 days I decided to do a fresh install because of some mistakes I made.  After the install I found that my drives that were labeled "data1" and "data3" had to be mounted in  the /media folder. Before the install they were auto-mounted upon boot. My fstab file has changed significantly from having a description above each UUID to just the UUIDs and other pertinent information ```
proc            /proc           proc    defaults        0       0
UUID=18d56e90-95f5-4c0f-bdc9-99f5a0941c5b /               ext3    relatime,errors=remount-ro 0       1
UUID=52e05ef7-5c63-40eb-bedf-2cc110165ef3 /home           ext3    relatime        0       2
UUID=4d8fc242-f47d-4368-bb2d-250bc986f2a7 /tmp            ext3    relatime        0       2
UUID=3873da43-e79e-4bbf-a816-37077c43504e /var            ext3    relatime        0       2
UUID=69c7cd33-b452-4582-abc7-e2452f60c853 none            swap    sw              0       0
UUID=0ef04929-7a1a-4db6-b965-32430de084e4 none            swap    sw              0       0
UUID=76725399-741f-4f87-b424-29a41e4fb620 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
``` I tried installing "psydm" but when I choose a certian partition it ask about another partition.
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39b79b14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         997     8008371   82  Linux swap / Solaris
/dev/sda2             998       30401   236187630   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a7273

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         997     8008371   82  Linux swap / Solaris
/dev/sdb2             998       60801   480375630   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf42bf42b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5227    41985846    7  HPFS/NTFS
/dev/sdc2            5228        6260     8297572+  82  Linux swap / Solaris
/dev/sdc3            6261        8692    19535040   83  Linux
/dev/sdc4            8693       19457    86469862+   5  Extended
/dev/sdc5            8693       10880    17575078+  83  Linux
/dev/sdc6           10881       13312    19535008+  83  Linux
/dev/sdc7           13313       19457    49359681   83  Linux

```

```
 ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 240 2008-11-21 15:27 .
drwxr-xr-x 6 root root 120 2008-11-21 10:00 ..
lrwxrwxrwx 1 root root  10 2008-11-21 15:27 066fbafd-a411-4393-9d14-ee046e545d48 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-11-21 10:00 0ef04929-7a1a-4db6-b965-32430de084e4 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-11-21 15:27 13761ed2-0c9d-407f-93d3-dee1dc678db5 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2008-11-21 10:00 18d56e90-95f5-4c0f-bdc9-99f5a0941c5b -> ../../sdc3
lrwxrwxrwx 1 root root  10 2008-11-21 10:00 3873da43-e79e-4bbf-a816-37077c43504e -> ../../sdc6
lrwxrwxrwx 1 root root  10 2008-11-21 10:00 4d8fc242-f47d-4368-bb2d-250bc986f2a7 -> ../../sdc5
lrwxrwxrwx 1 root root  10 2008-11-21 10:00 52e05ef7-5c63-40eb-bedf-2cc110165ef3 -> ../../sdc7
lrwxrwxrwx 1 root root  10 2008-11-21 15:27 60F8DE0D7C611AF2 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-11-21 10:00 69c7cd33-b452-4582-abc7-e2452f60c853 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-11-21 10:00 76725399-741f-4f87-b424-29a41
```
             
                              This is /sdc
```

Device: UUID=69c7cd33-b452-4582-abc7-e2452f60c853
Mount point: swap
File system: swap
Options: sw
Dump flag: 0
Fsck value: 0

Device: UUID=0ef04929-7a1a-4db6-b965-32430de084e4
Mount point: swap
File system: swap
Options: sw
Dump flag: 0
Fsck value: 0

Device: UUID=76725399-741f-4f87-b424-29a41e4fb620
Mount point: swap
File system: swap
Options: sw
Dump flag: 0
Fsck value: 0

Device: UUID=18d56e90-95f5-4c0f-bdc9-99f5a0941c5b
Mount point: /
File system: ext3
Options: defaults
Dump flag: 0
Fsck value: 1

Device: UUID=4d8fc242-f47d-4368-bb2d-250bc986f2a7
Mount point: /tmp
File system: ext3
Options: defaults
Dump flag: 0
Fsck value: 2

Device: UUID=3873da43-e79e-4bbf-a816-37077c43504e
Mount point: /var
File system: ext3
Options: defaults
Dump flag: 0
Fsck value: 2

Device: UUID=52e05ef7-5c63-40eb-bedf-2cc110165ef3
Mount point: /home
File system: ext3
Options: defaults
Dump flag: 0
Fsck value: 2

Device: UUID=066fbafd-a411-4393-9d14-ee046e545d48
Mount point: /media/data1
File system: ext3
Options: defaults
Dump flag: 0
Fsck value: 0

Device: UUID=13761ed2-0c9d-407f-93d3-dee1dc678db5
Mount point: Unknown
File system: ext3
Options: defaults
Dump flag: 0
Fsck value: 0

Device: UUID=60F8DE0D7C611AF2
Mount point: Unknown
File system: ntfs
Options: defaults
Dump flag: 0
Fsck value: 0

``` 
Here is my previous /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system>                         <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=ec7afbfd-c833-4b9d-a204-a3522a24d843 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=066fbafd-a411-4393-9d14-ee046e545d48 /data-1         ext3    relatime        0       2
# /dev/sdb2
UUID=13761ed2-0c9d-407f-93d3-dee1dc678db5 /data-3         ext3    relatime        0       2
# /dev/hda7
UUID=c8fd2408-59a5-4383-b36d-5b524b267c7c /home           ext3    relatime        0       2
# /dev/hda5
UUID=ada46972-e221-4b43-a9f9-93461f0e7e2e /tmp            ext3    relatime        0       2
# /dev/hda6
UUID=b0678449-5ca5-485d-a63a-69485c70c54f /var            ext3    relatime        0       2
# /dev/hda2
UUID=dccc8a13-1826-4939-b104-38bd26db51f8 none            swap    sw              0       0
# /dev/sda1
UUID=69c7cd33-b452-4582-abc7-e2452f60c853 none            swap    sw              0       0
# /dev/sdb1
UUID=0ef04929-7a1a-4db6-b965-32430de084e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=128,devmode=664 0 0 
```

When I attempted to change directorys for /sda2 it informed me that there was no such directory so I am doing something wrong. Thank you for any help.:confused:

            Ktechman

---

### Post by bodhi.zazen on 2008-11-21
> **ktechman said:**
> When I attempted to change directorys for /sda2 it informed me that there was no such directory so I am doing something wrong. Thank you for any help.:confused:

            Ktechman

no, you just need to make the mount point.

I suggest you change "/data-1" to either something more meaningful (if you wish) or to /media or /mnt.

Assuming you do not wish to change :

```
sudo mkdir /data1
```

Then it should mount.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

