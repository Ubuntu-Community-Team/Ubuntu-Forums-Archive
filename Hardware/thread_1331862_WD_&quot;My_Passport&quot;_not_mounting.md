---
title: "WD &quot;My Passport&quot; not mounting"
date: 2009-11-19
forum: Hardware
---

### Post by jaunty-user on 2009-11-19
Hi All,

Invested in a 320gig WD "My Passport". I plugged it in  and ran fdisk -l to see where the drive appears. It didn't appear in fdisk, just my two hard drives (see below). I checked dmseg but can't make head nor tail of what the problem is, any ideas??? 

Any help much appriciated - thanks!

Jaunty-user

------------------
dmesg

[ 1390.500065] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 1390.646844] usb 1-1: configuration #1 chosen from 1 choice
[ 1390.693236] Initializing USB Mass Storage driver...
[ 1390.693523] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1390.693667] usb-storage: device found at 5
[ 1390.693674] usb-storage: waiting for device to settle before scanning
[ 1390.693681] usbcore: registered new interface driver usb-storage
[ 1390.693687] USB Mass Storage support registered.
[ 1395.692255] usb-storage: device scan complete
[ 1395.692687] scsi 8:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[ 1396.105352] sd 8:0:0:0: [sdc] 1003520 512-byte hardware sectors: (513 MB/490 MiB)
[ 1396.105871] sd 8:0:0:0: [sdc] Write Protect is off
[ 1396.105879] sd 8:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1396.105884] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 1396.109605] sd 8:0:0:0: [sdc] 1003520 512-byte hardware sectors: (513 MB/490 MiB)
[ 1396.110086] sd 8:0:0:0: [sdc] Write Protect is off
[ 1396.110091] sd 8:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1396.110095] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 1396.110104]  sdc: sdc1
[ 1396.111096] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 1396.111211] sd 8:0:0:0: Attached scsi generic sg4 type 0
[ 1408.454555] usb 1-1: USB disconnect, address 5
----------------

root@al:~# cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=a27564cf-857d-40c0-9501-f81b3edb2d82 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=061ed075-843c-40b5-a3ba-cb27a39799eb /home           ext3    relatime        0       2
# /storage was on /dev/sdb1 during installation
UUID=19a2f0e8-cbdd-471e-afe5-87f1dc01c0c3 /storage        ext3    relatime        0       2
# swap was on /dev/sda1 during installation
UUID=f4aa430a-4488-4ff5-aa7b-c4de3bc6cdf2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


------------------------
root@al:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19a2abeb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         973     7815591   82  Linux swap / Solaris
/dev/sda2   *         974       13131    97659135   83  Linux
/dev/sda3           13132       60801   382909275   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001ee9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

---

