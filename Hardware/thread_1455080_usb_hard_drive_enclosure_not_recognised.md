---
title: "usb hard drive enclosure not recognised"
date: 2010-04-15
forum: Hardware
---

### Post by karmicgaz on 2010-04-15
Got a usb hard drive enclosure to make use of an old drive as storage, plugged it in first time no probs, automounted on desktop, decided to format, within moments of starting format (fat) closed and disappeared from desktop, and now will not automount at all. This was an old xp drive and I include the last few lines from dmesg.
Help please!

[ 75.237555] lib80211_crypt: registered algorithm 'TKIP'
[ 125.064159] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 125.198249] usb 1-3: configuration #1 chosen from 1 choice
[ 125.289392] Initializing USB Mass Storage driver...
[ 125.291657] scsi2 : SCSI emulation for USB Mass Storage devices
[ 125.292128] usbcore: registered new interface driver usb-storage
[ 125.292139] USB Mass Storage support registered.
[ 125.302417] usb-storage: device found at 2
[ 125.302421] usb-storage: waiting for device to settle before scanning
[ 130.300415] usb-storage: device scan complete
[ 130.301282] scsi 2:0:0:0: Direct-Access HDS72808 0PLAT20 A21B PQ: 0 ANSI: 2 CCS
[ 130.302538] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 130.322036] sd 2:0:0:0: [sdb] 160836480 512-byte logical blocks: (82.3 GB/76.6 GiB)
[ 130.322922] sd 2:0:0:0: [sdb] Write Protect is off
[ 130.322927] sd 2:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 130.322931] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 130.324756] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 130.324763] sdb: sdb1
[ 130.351124] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 130.351136] sd 2:0:0:0: [sdb] Attached SCSI disk
gaz@gaz-laptop:~$

---

### Post by ajgreeny on 2010-04-15
Is it recognised by ```
sudo fdisk -l
``` when you plug it in and run that command?

It would appear that the formatting went awry for some reason, so perhaps worth formatting again, after deleting the currently bad formated partition.

---

### Post by karmicgaz on 2010-04-17
will try tomorrow and post result, thanks.

---

### Post by karmicgaz on 2010-04-18
This is what I got.
sk identifier: 0x19c719c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18729   150440661   83  Linux
/dev/sda2           18730       19457     5847660    5  Extended
/dev/sda5           18730       19457     5847628+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x009d009d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95e795e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       10010    80405293+   7  HPFS/NTFS

---

### Post by karmicgaz on 2010-04-20
Could it be because it's ntfs? I seem to recall in windows when converting to ntfs you can't go back to fat?

---

