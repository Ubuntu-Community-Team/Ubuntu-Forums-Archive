---
title: "How do I mount this?"
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by knichel on 2006-01-16
I am trying to get my firewire 30G 3rd generation iPod mounted under ubuntu 5.10.  I am not having any luck. 

Result of dmesg (in regards to the 1394 lines)...
[4294724.819000] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
[4294724.820000] sbp2: probe of 000a2700020f5938-0 failed with error -16
[4294724.826000] scsi4 : SCSI emulation for IEEE-1394 SBP-2 Devices
[4294746.030000] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
[4294746.031000] sbp2: probe of 000a2700020f5938-0 failed with error -16
[4294824.465000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[4294824.465000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a2700020f5938]
[4294846.738000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[4294846.738000] ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[000a2700020f5938]
[4294846.738000] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[4294846.996000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[4294846.996000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[4294846.997000] scsi5 : SCSI emulation for IEEE-1394 SBP-2 Devices
[4294868.212000] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
[4294868.213000] sbp2: probe of 000a2700020f5938-0 failed with error -16



Result of fdisk -l
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2       14358   115322602+   f  W95 Ext'd (LBA)
/dev/hda2   *       14359       19457    40957686    7  HPFS/NTFS
/dev/hda5               2         263     2104483+  82  Linux swap / Solaris
/dev/hda6             264        4088    30724281   83  Linux
/dev/hda7            4089       14358    82493743+   b  W95 FAT32



My fstab file...
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hda7       /media/hda7     vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda7       /media/windows  vfat    umask=0222      0       0
/dev/sdc2       /media/iPod  vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8       0 0

I would appreciate any assistance you can give.  I really want to divorce from Microsoft.

--
Mike

---

