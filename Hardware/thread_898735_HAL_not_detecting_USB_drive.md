---
title: "HAL not detecting USB drive"
date: 2008-08-23
forum: Hardware
---

### Post by nixscripter on 2008-08-23
Hello everyone. I hope this is the right forum for this post.

The short version is that, for some reason, one of my USB external hard drives is being detected by HAL, and properly mounted by **gnome-mount** when it is plugged in. The other one isn't -- after what I did to it.

The first drive: Micronet 320 GB
Second drive: Segate Free Agent 500 GB.

Here's the long version:

The first drive worked well for quite a while. Being a leftover from my Macintosh days, it's formatted HFS+. The only drawback is that, whenever I unplug it too fast, I have to go find a Mac to run fsck on it.

But the second one is new. For the first time, I plugged in, and it automatically mounted a Mac partiton. It's formatted for Mac and Windows (somehow), both NTFS and HFS+, using the whole disk. I said to myself, forget this, I want XFS for other reasons.

So, I ejected it from the desktop, and did:
```

$ **fdisk -l /dev/sdb**

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  HPFS/NTFS

```

Huh? I thought it was HFS! But I ignored this oddity and went on. I erased it by deleting that partition, adding a Linux partition of equal size (the entire disk), and re-wrote the DOS partition table. I got some error about reloading the partition table in the kernel failing due to "permission denied", meaning it would use the old table until reboot. But I figured that's because I forgot to switch to root user when I did this, and it was no big deal.

So, I unplugged it. No problem. I plugged it back in. Nothing happened. 

**/dev/sdb** and **/dev/sdb1** were back, though, which disappeared when I unplugged it. So, I made the XFS filesystem I wanted (with mkfs -f to overwrite the NTFS it wanted to preserve) on sdb1. I then tried to tell gnome to mount again:

```

$ **gnome-mount -d /dev/sdb1**
gnome-mount 0.6
$ **echo $?**
1
$

```

Needless to say, it didn't appear.

I mounted manually (with the **mount** command), which was fine; chowned it to my user; synced all disks; unplugged it, and plugged back in. **/dev/sdb** and **/dev/sdb1** reappeared, but gnome-mount still did nothing about it, manually or automatically.

So, I took the advice of **fdisk** and rebooted, unplugging it after shutdown.

I logged back in, and plugged it in. Nothing. **dmesg** said:
```

[  159.852000] usb 2-1: new high speed USB device using ehci_hcd and address 2
[  160.000000] usb 2-1: configuration #1 chosen from 1 choice
[  160.272000] usbcore: registered new interface driver libusual
[  160.496000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  160.496000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  160.504000] Initializing USB Mass Storage driver...
[  160.504000] scsi5 : SCSI emulation for USB Mass Storage devices
[  160.504000] usb-storage: device found at 2
[  160.504000] usb-storage: waiting for device to settle before scanning
[  160.504000] usbcore: registered new interface driver usb-storage
[  160.504000] USB Mass Storage support registered.
[  165.504000] usb-storage: device scan complete
[  165.504000] scsi 5:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100F PQ: 0 ANSI: 4
[  173.604000] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  173.608000] sd 5:0:0:0: [sdb] Write Protect is off
[  173.608000] sd 5:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[  173.608000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  173.608000] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  173.612000] sd 5:0:0:0: [sdb] Write Protect is off
[  173.612000] sd 5:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[  173.612000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  173.612000]  sdb: sdb1
[  173.668000] sd 5:0:0:0: [sdb] Attached SCSI disk
[  173.668000] sd 5:0:0:0: Attached scsi generic sg2 type 0

```

so I thought that was okay. But here's the thing. When I plugged in the second disk, and it appeared, I remembered that gnome-mount is just a front-end to HAL. So I looked at the second disk:

```

$ **lshal | grep sdc**
  block.device = '/dev/sdc'  (string)
  linux.sysfs_path = '/sys/block/sdc'  (string)
  block.device = '/dev/sdc3'  (string)
  linux.sysfs_path = '/sys/block/sdc/sdc3'  (string)
  block.device = '/dev/sdc2'  (string)
  linux.sysfs_path = '/sys/block/sdc/sdc2'  (string)
  block.device = '/dev/sdc4'  (string)
  linux.sysfs_path = '/sys/block/sdc/sdc4'  (string)
  block.device = '/dev/sdc1'  (string)
  linux.sysfs_path = '/sys/block/sdc/sdc1'  (string)

```

But for the first disk:
```

$ **lshal | grep sdb**
$ 

```

So HAL didn't register it, which is why gnome-mount doesn't know about it. 

I can still mount it manually. I just want to know why HAL isn't telling gnome-mount to mount it automatically. 

Hopefully, that story wasn't too convoluted. Any suggestions?

---

