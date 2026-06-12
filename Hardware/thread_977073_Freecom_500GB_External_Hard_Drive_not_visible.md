---
title: "Freecom 500GB External Hard Drive not visible"
date: 2008-11-09
forum: Hardware
---

### Post by gilbertt on 2008-11-09
I've bought a new Freecom 500GB external hard drive (formatted as ntfs) which is visible in Windows, but which isn't getting on with Ubuntu at all. First it was automatically detected, then it was mounted but not accessible, now as far as Ubuntu is concerned it simply isn't there. I've trawled the forums and tried a few things, but no joy yet:

My fstab file reads: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 ntfs ro,auto,user,fmask=0111,dmask=0000
#Added by diskmounter utility
/dev/hdb3 /media/hdb3 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
/dev/hdd1 /media/hdd1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0


sudo fdisk -l reads:

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3772    30298558+   7  HPFS/NTFS
/dev/hdb2            3773        3835      506047+  82  Linux swap / Solaris
/dev/hdb3            3836        7475    29238300    c  W95 FAT32 (LBA)

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        7175    57633156    c  W95 FAT32 (LBA)
/dev/hdd2   *        7176        9621    19647495   83  Linux
/dev/hdd3            9622        9729      867510    5  Extended
/dev/hdd5            9622        9729      867478+  82  Linux swap / Solaris

ls -l reads:

lrwxrwxrwx  1 root   root       6 2007-08-22 00:22 cdrom -> cdrom0
drwxr-xr-x  2 root   root    4096 2007-08-22 00:22 cdrom0
dr-xr-xr-x  1 root   root   45056 2008-11-03 22:36 hdb1
drwxr-xr-x  9 chelly chelly 16384 1970-01-01 01:00 hdb3
drwxr-xr-x 19 chelly chelly 32768 1970-01-01 01:00 hdd1

dmesg seems to give some indication of whats going on, but I can't decipher it: 

[17182132.172000] usb 3-6: new high speed USB device using ehci_hcd and address 31[17182132.304000] scsi1 : SCSI emulation for USB Mass Storage devices
[17182132.304000] usb-storage: device found at 31
[17182132.304000] usb-storage: waiting for device to settle before scanning
[17182137.304000]   Vendor: SAMSUNG   Model: HD501LJ           Rev:
[17182137.304000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17182137.304000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[17182137.304000] sda: assuming drive cache: write through
[17182137.308000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[17182137.308000] sda: assuming drive cache: write through
[17182137.308000]  sda: sda1
[17182137.368000] sd 1:0:0:0: Attached scsi disk sda
[17182137.368000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17182137.368000] usb-storage: device scan complete
[17182383.652000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17182383.652000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17182387.252000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17182387.252000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17182393.460000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17182393.460000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17182399.496000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17182399.496000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17182903.100000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17182903.100000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17182908.688000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17182908.688000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17182958.532000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17182958.532000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17183939.048000] usb 3-6: USB disconnect, address 31
[17183951.700000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17183951.700000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17183961.088000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17183961.088000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

Can someone give the benefit of their wisdom to a floundering novice?

Thanks,
G

---

### Post by taurus on 2008-11-09
What happens when you run these from a terminal?

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
df -h
```

---

### Post by gilbertt on 2008-11-11
When I ran this:

sudo mount -t ntfs-3g /dev/sda1 /media/sda1

I got this:

unknown filesystem type 'ntfs-3g'


I also tried this:

sudo mount -t ntfs /dev/sda1 /media/sda1

but got this:

mount: special device /dev/sda1 does not exist

---

