---
title: "USB thumb drive not automounting in Karmic"
date: 2010-03-02
forum: Hardware
---

### Post by dnairb on 2010-03-02
I have an issue on a fresh install of Ubuntu 9.10, Karmic.
I installed a cli system initially from the alternate Karmic 64-bit cd. I then installed ubuntu-desktop with the --no-install-recommends flag.
After rebooting, I tried a USB thumb drive, which was recognised by the system but not automounted. I then installed usbount and psmount, and checked that hal is installed.
I have the correct settings in Configuration editor.

I checked dmesg before and after inserting the drive; the "after" messages were:

```
[  100.690036] usb 1-6: new high speed USB device using ehci_hcd and address 5
[  100.841568] usb 1-6: configuration #1 chosen from 1 choice
[  101.014227] Initializing USB Mass Storage driver...
[  101.014852] scsi6 : SCSI emulation for USB Mass Storage devices
[  101.015148] usb-storage: device found at 5
[  101.015155] usb-storage: waiting for device to settle before scanning
[  101.015175] usbcore: registered new interface driver usb-storage
[  101.015183] USB Mass Storage support registered.
[  106.011303] usb-storage: device scan complete
[  106.013320] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[  106.014454] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  106.022245] sd 6:0:0:0: [sdb] 3940479 512-byte logical blocks: (2.01 GB/1.87 GiB)
[  106.023218] sd 6:0:0:0: [sdb] Write Protect is off
[  106.023227] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  106.023234] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  106.027195] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  106.027208]  sdb: sdb1
[  106.034400] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  106.034416] sd 6:0:0:0: [sdb] Attached SCSI removable disk
```

..which is the same output on a different system which *does* automount the usb thumb drive. (This other system was installed using the livecd)

I can only think that the the --no-install-recommends flag prevented the installation of something that is needed to automount the usb drive.

---

### Post by dnairb on 2010-03-06
I "solved" this by performing a full install of ubuntu-desktop (along with all the reccomends), then removing all the stuff I didn't want. USB thumb drives are now automounted when inserted.

I still don't know what app or module was missing from the --no-install-reccomends install.

---

