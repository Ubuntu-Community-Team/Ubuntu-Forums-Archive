---
title: "How to power off external USB hard disk?"
date: 2008-08-07
forum: General Help
---

### Post by rikxik on 2008-08-07
Hi,

I'm using gutsy:

> $ uname -a
Linux loki 2.6.22-15-generic #1 SMP Fri Jul 11 19:25:33 UTC 2008 i686 GNU/Linux

When I plug in my USB external hard disk (while gutsy is running), I don't see any icon pop-up in the panel/desktop. However, dmesg shows this:

> 
[ 1168.948000] usb 5-6: new high speed USB device using ehci_hcd and address 6
[ 1169.080000] usb 5-6: configuration #1 chosen from 1 choice
[ 1169.164000] usbcore: registered new interface driver libusual
[ 1169.232000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 1169.232000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 1169.236000] Initializing USB Mass Storage driver...
[ 1169.236000] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1169.236000] usb-storage: device found at 6
[ 1169.236000] usb-storage: waiting for device to settle before scanning
[ 1169.236000] usbcore: registered new interface driver usb-storage
[ 1169.236000] USB Mass Storage support registered.
[ 1174.240000] usb-storage: device scan complete
[ 1174.240000] scsi 6:0:0:0: Direct-Access     Hitachi  HTS542512K9SA00       PQ: 0 ANSI: 2 CCS
[ 1174.244000] sd 6:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[ 1174.244000] sd 6:0:0:0: [sdb] Write Protect is off
[ 1174.244000] sd 6:0:0:0: [sdb] Mode Sense: 3c 00 00 00
[ 1174.244000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1174.244000] sd 6:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[ 1174.244000] sd 6:0:0:0: [sdb] Write Protect is off
[ 1174.244000] sd 6:0:0:0: [sdb] Mode Sense: 3c 00 00 00
[ 1174.244000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1174.244000]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 sdb7 sdb8 sdb9 sdb10 sdb11 sdb12 sdb13 sdb14 sdb15 > sdb4
[ 1174.420000] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 1174.420000] sd 6:0:0:0: Attached scsi generic sg2 type 0


The drive light goes ON and fdisk -l /dev/sdb shows the partition etc. So the drive is detected fine. Note that none of the partitions on the external drive have been mounted - so there is nothing to umount. Now if I want to disconnect the drive, I would have to swith it off first. There is no hardware power-off switch on the drive. How to switch it off so that I can safely remove it (except shutting the laptop down)?

I have also tried "sudo eject /dev/sdb..." commands. No error, no dmesg output - but the drive light stays on so it doesn't seem to be working.

Anybody seen this before?

---

### Post by Krupski on 2008-08-07
> **rikxik said:**
> ...So the drive is detected fine. Note that none of the partitions on the external drive have been mounted - so there is nothing to umount. Now if I want to disconnect the drive, I would have to swith it off first....

If it's not mounted, simply unplug the USB cable from the computer and the drive will power down.

I recommend unplugging the USB cable from the COMPUTER rather than from the RUNNING HARD DRIVE to avoid bumping or jarring the drive while it's spinning.

If you DID mount the drive, just do a 'sync', then umount it, then unplug it.

-- Roger

---

