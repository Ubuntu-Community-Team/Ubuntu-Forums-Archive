---
title: "USB mass storage device unmounts after period of inactivity"
date: 2009-11-02
forum: Hardware
---

### Post by canas on 2009-11-02
Hello, 
Ever since upgrading to karmic over the past weekend, I've been having issues a large, NTFS formatted USB hard drive.  Before I describe the problem let me start by saying this hard drive is less than a year old and worked perfectly with Jaunty and continues to work fine in Mac OS X and Windows XP.  Under Karmic, however, after about 20 minutes of being connected and inactive, the device becomes inaccessible due to an input/output error.  I've tried plugging it into multiple USB slots and cards on 2 different pcs running Karmic, but get the same problem.  Here's a copy of some relavant portions of system logs starting with the connection of the device:

```

Nov  2 17:34:36 suigintou kernel: [ 1401.704268] usb 1-3: USB disconnect, address 5
Nov  2 17:34:43 suigintou kernel: [ 1409.136060] usb 1-3: new high speed USB device using ehci_hcd and address 6
Nov  2 17:34:44 suigintou kernel: [ 1409.336225] usb 1-3: configuration #1 chosen from 1 choice
Nov  2 17:35:14 suigintou kernel: [ 1439.750647] usb 1-3: USB disconnect, address 6
Nov  2 17:35:25 suigintou kernel: [ 1450.688071] usb 1-3: new high speed USB device using ehci_hcd and address 7
Nov  2 17:35:25 suigintou kernel: [ 1450.837161] usb 1-3: configuration #1 chosen from 1 choice
Nov  2 17:35:25 suigintou kernel: [ 1451.043337] Initializing USB Mass Storage driver...
Nov  2 17:35:25 suigintou kernel: [ 1451.046742] scsi2 : SCSI emulation for USB Mass Storage devices
Nov  2 17:35:25 suigintou kernel: [ 1451.047226] usbcore: registered new interface driver usb-storage
Nov  2 17:35:25 suigintou kernel: [ 1451.047238] USB Mass Storage support registered.
Nov  2 17:35:25 suigintou kernel: [ 1451.049010] usb-storage: device found at 7
Nov  2 17:35:25 suigintou kernel: [ 1451.049019] usb-storage: waiting for device to settle before scanning
Nov  2 17:35:30 suigintou kernel: [ 1456.049700] usb-storage: device scan complete
Nov  2 17:35:30 suigintou kernel: [ 1456.060286] scsi 2:0:0:0: Direct-Access     Seagate  FreeAgent XTreme 4113 PQ: 0 ANSI: 4
Nov  2 17:35:30 suigintou kernel: [ 1456.060956] sd 2:0:0:0: Attached scsi generic sg1 type 0
Nov  2 17:35:30 suigintou kernel: [ 1456.068731] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Nov  2 17:35:30 suigintou kernel: [ 1456.070473] sd 2:0:0:0: [sdb] Write Protect is off
Nov  2 17:35:30 suigintou kernel: [ 1456.070481] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
Nov  2 17:35:30 suigintou kernel: [ 1456.070486] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Nov  2 17:35:30 suigintou kernel: [ 1456.085875] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Nov  2 17:35:30 suigintou kernel: [ 1456.085888]  sdb: sdb1
Nov  2 17:35:30 suigintou kernel: [ 1456.136108] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Nov  2 17:35:30 suigintou kernel: [ 1456.136119] sd 2:0:0:0: [sdb] Attached SCSI disk
Nov  2 17:35:34 suigintou ntfs-3g[3769]: Version 2009.4.4 external FUSE 27
Nov  2 17:35:34 suigintou ntfs-3g[3769]: Mounted /dev/sdb1 (Read-Write, label "FreeAgent Xtreme", NTFS 3.1)
Nov  2 17:35:34 suigintou ntfs-3g[3769]: Cmdline options: rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077
Nov  2 17:35:34 suigintou ntfs-3g[3769]: Mount options: rw,nosuid,nodev,uhelper=devkit,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sdb1,blkdev,blksize=4096
Nov  2 17:36:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:38:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:39:01 suigintou CRON[3845]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov  2 17:40:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:42:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:44:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:46:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:48:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:50:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:52:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:54:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:56:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 17:58:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:00:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:02:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:04:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:06:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:08:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:09:01 suigintou CRON[3889]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov  2 18:10:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:12:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:12:39 suigintou kernel: [ 3685.112137] usb 1-3: reset high speed USB device using ehci_hcd and address 7
Nov  2 18:12:55 suigintou kernel: [ 3700.224079] usb 1-3: device descriptor read/64, error -110
Nov  2 18:13:10 suigintou kernel: [ 3715.440088] usb 1-3: device descriptor read/64, error -110
Nov  2 18:13:10 suigintou kernel: [ 3715.656286] usb 1-3: reset high speed USB device using ehci_hcd and address 7
Nov  2 18:13:25 suigintou kernel: [ 3730.768084] usb 1-3: device descriptor read/64, error -110
Nov  2 18:13:40 suigintou kernel: [ 3745.984107] usb 1-3: device descriptor read/64, error -110
Nov  2 18:13:40 suigintou kernel: [ 3746.201377] usb 1-3: reset high speed USB device using ehci_hcd and address 7
Nov  2 18:13:45 suigintou kernel: [ 3751.220177] usb 1-3: device descriptor read/8, error -110
Nov  2 18:13:51 suigintou kernel: [ 3756.341818] usb 1-3: device descriptor read/8, error -110
Nov  2 18:13:51 suigintou kernel: [ 3756.556265] usb 1-3: reset high speed USB device using ehci_hcd and address 7
Nov  2 18:13:56 suigintou kernel: [ 3761.576142] usb 1-3: device descriptor read/8, error -110
Nov  2 18:14:01 suigintou kernel: [ 3766.696162] usb 1-3: device descriptor read/8, error -110
Nov  2 18:14:01 suigintou kernel: [ 3766.800147] sd 2:0:0:0: Device offlined - not ready after error recovery
Nov  2 18:14:01 suigintou kernel: [ 3766.801330] usb 1-3: USB disconnect, address 7
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou kernel: [ 3766.964103] usb 1-3: new high speed USB device using ehci_hcd and address 8
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:01 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:14:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:16 suigintou kernel: [ 3782.076089] usb 1-3: device descriptor read/64, error -110
Nov  2 18:14:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:32 suigintou kernel: [ 3797.292124] usb 1-3: device descriptor read/64, error -110
Nov  2 18:14:32 suigintou kernel: [ 3797.509136] usb 1-3: new high speed USB device using ehci_hcd and address 9
Nov  2 18:14:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:47 suigintou kernel: [ 3812.620074] usb 1-3: device descriptor read/64, error -110
Nov  2 18:14:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:14:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:14:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:02 suigintou kernel: [ 3827.836502] usb 1-3: device descriptor read/64, error -110
Nov  2 18:15:02 suigintou kernel: [ 3828.052129] usb 1-3: new high speed USB device using ehci_hcd and address 10
Nov  2 18:15:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:07 suigintou kernel: [ 3833.072284] usb 1-3: device descriptor read/8, error -110
Nov  2 18:15:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:12 suigintou kernel: [ 3838.192267] usb 1-3: device descriptor read/8, error -110
Nov  2 18:15:13 suigintou kernel: [ 3838.408094] usb 1-3: new high speed USB device using ehci_hcd and address 11
Nov  2 18:15:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:18 suigintou kernel: [ 3843.428269] usb 1-3: device descriptor read/8, error -110
Nov  2 18:15:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:23 suigintou kernel: [ 3848.548245] usb 1-3: device descriptor read/8, error -110
Nov  2 18:15:23 suigintou kernel: [ 3848.652423] hub 1-0:1.0: unable to enumerate USB device on port 3
Nov  2 18:15:23 suigintou kernel: [ 3848.924074] usb 3-1: new full speed USB device using uhci_hcd and address 2
Nov  2 18:15:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:38 suigintou kernel: [ 3864.036094] usb 3-1: device descriptor read/64, error -110
Nov  2 18:15:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:54 suigintou kernel: [ 3879.252105] usb 3-1: device descriptor read/64, error -110
Nov  2 18:15:54 suigintou kernel: [ 3879.468679] usb 3-1: new full speed USB device using uhci_hcd and address 3
Nov  2 18:15:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:15:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:15:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:16:09 suigintou kernel: [ 3894.580090] usb 3-1: device descriptor read/64, error -110
Nov  2 18:16:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:24 suigintou kernel: [ 3909.800070] usb 3-1: device descriptor read/64, error -110
Nov  2 18:16:24 suigintou kernel: [ 3910.016064] usb 3-1: new full speed USB device using uhci_hcd and address 4
Nov  2 18:16:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:28 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:28 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:28 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:28 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:28 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:28 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:29 suigintou kernel: [ 3915.037176] usb 3-1: device descriptor read/8, error -110
Nov  2 18:16:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:31 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:31 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:34 suigintou kernel: [ 3920.157427] usb 3-1: device descriptor read/8, error -110
Nov  2 18:16:35 suigintou kernel: [ 3920.372101] usb 3-1: new full speed USB device using uhci_hcd and address 5
Nov  2 18:16:35 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:35 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:39 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:39 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:40 suigintou kernel: [ 3925.393649] usb 3-1: device descriptor read/8, error -110
Nov  2 18:16:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:43 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:43 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:45 suigintou kernel: [ 3930.513891] usb 3-1: device descriptor read/8, error -110
Nov  2 18:16:45 suigintou kernel: [ 3930.616094] hub 3-0:1.0: unable to enumerate USB device on port 1
Nov  2 18:16:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:47 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:47 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:51 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:51 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:55 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:55 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:16:59 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:16:59 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:01 suigintou CRON[3917]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  2 18:17:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:03 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:03 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:07 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:07 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:11 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:11 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:15 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:15 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:19 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:19 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:23 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:23 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:27 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:27 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:31 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:31 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:35 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:35 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:39 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:39 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:43 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:43 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:47 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:47 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:17:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:17:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:18:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:18:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:18:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:19:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:19:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:20:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:20:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:20:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:21:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:21:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:22:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:22:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:22:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:23:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:23:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:07 suigintou wpa_supplicant[1386]: CTRL-EVENT-SCAN-RESULTS 
Nov  2 18:24:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:50 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:50 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:54 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:54 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:24:58 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:24:58 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:02 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:02 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:06 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:06 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:10 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:10 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:14 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:14 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:18 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:18 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:22 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:22 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:26 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:26 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:30 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:30 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:34 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:34 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:38 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:38 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:42 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:42 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:46 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:46 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:47 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:47 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:47 suigintou ntfs-3g[3769]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov  2 18:25:47 suigintou ntfs-3g[3769]: Failed to read of MFT, mft=5 count=1 br=-1: Input/output error
Nov  2 18:25:49 suigintou ntfs-3g[3769]: Unmounting /dev/sdb1 (FreeAgent Xtreme)

```
```

Nov  2 17:33:43 suigintou kernel: [ 1348.704082] usb 1-3: new high speed USB device using ehci_hcd and address 5
Nov  2 17:33:43 suigintou kernel: [ 1348.857465] usb 1-3: configuration #1 chosen from 1 choice
Nov  2 17:34:36 suigintou kernel: [ 1401.704268] usb 1-3: USB disconnect, address 5
Nov  2 17:34:43 suigintou kernel: [ 1409.136060] usb 1-3: new high speed USB device using ehci_hcd and address 6
Nov  2 17:34:44 suigintou kernel: [ 1409.336225] usb 1-3: configuration #1 chosen from 1 choice
Nov  2 17:35:14 suigintou kernel: [ 1439.750647] usb 1-3: USB disconnect, address 6
Nov  2 17:35:25 suigintou kernel: [ 1450.688071] usb 1-3: new high speed USB device using ehci_hcd and address 7
Nov  2 17:35:25 suigintou kernel: [ 1450.837161] usb 1-3: configuration #1 chosen from 1 choice
Nov  2 17:35:25 suigintou kernel: [ 1451.043337] Initializing USB Mass Storage driver...
Nov  2 17:35:25 suigintou kernel: [ 1451.046742] scsi2 : SCSI emulation for USB Mass Storage devices
Nov  2 17:35:25 suigintou kernel: [ 1451.047226] usbcore: registered new interface driver usb-storage
Nov  2 17:35:25 suigintou kernel: [ 1451.047238] USB Mass Storage support registered.
Nov  2 17:35:25 suigintou kernel: [ 1451.049010] usb-storage: device found at 7
Nov  2 17:35:25 suigintou kernel: [ 1451.049019] usb-storage: waiting for device to settle before scanning
Nov  2 17:35:30 suigintou kernel: [ 1456.049700] usb-storage: device scan complete
Nov  2 17:35:30 suigintou kernel: [ 1456.060286] scsi 2:0:0:0: Direct-Access     Seagate  FreeAgent XTreme 4113 PQ: 0 ANSI: 4
Nov  2 17:35:30 suigintou kernel: [ 1456.060956] sd 2:0:0:0: Attached scsi generic sg1 type 0
Nov  2 17:35:30 suigintou kernel: [ 1456.068731] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Nov  2 17:35:30 suigintou kernel: [ 1456.070473] sd 2:0:0:0: [sdb] Write Protect is off
Nov  2 17:35:30 suigintou kernel: [ 1456.070481] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
Nov  2 17:35:30 suigintou kernel: [ 1456.070486] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Nov  2 17:35:30 suigintou kernel: [ 1456.085875] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Nov  2 17:35:30 suigintou kernel: [ 1456.085888]  sdb: sdb1
Nov  2 17:35:30 suigintou kernel: [ 1456.136108] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Nov  2 17:35:30 suigintou kernel: [ 1456.136119] sd 2:0:0:0: [sdb] Attached SCSI disk
Nov  2 18:12:39 suigintou kernel: [ 3685.112137] usb 1-3: reset high speed USB device using ehci_hcd and address 7
Nov  2 18:12:55 suigintou kernel: [ 3700.224079] usb 1-3: device descriptor read/64, error -110
Nov  2 18:13:10 suigintou kernel: [ 3715.440088] usb 1-3: device descriptor read/64, error -110
Nov  2 18:13:10 suigintou kernel: [ 3715.656286] usb 1-3: reset high speed USB device using ehci_hcd and address 7
Nov  2 18:13:25 suigintou kernel: [ 3730.768084] usb 1-3: device descriptor read/64, error -110
Nov  2 18:13:40 suigintou kernel: [ 3745.984107] usb 1-3: device descriptor read/64, error -110
Nov  2 18:13:40 suigintou kernel: [ 3746.201377] usb 1-3: reset high speed USB device using ehci_hcd and address 7
Nov  2 18:13:45 suigintou kernel: [ 3751.220177] usb 1-3: device descriptor read/8, error -110
Nov  2 18:13:51 suigintou kernel: [ 3756.341818] usb 1-3: device descriptor read/8, error -110
Nov  2 18:13:51 suigintou kernel: [ 3756.556265] usb 1-3: reset high speed USB device using ehci_hcd and address 7
Nov  2 18:13:56 suigintou kernel: [ 3761.576142] usb 1-3: device descriptor read/8, error -110
Nov  2 18:14:01 suigintou kernel: [ 3766.696162] usb 1-3: device descriptor read/8, error -110
Nov  2 18:14:01 suigintou kernel: [ 3766.800147] sd 2:0:0:0: Device offlined - not ready after error recovery
Nov  2 18:14:01 suigintou kernel: [ 3766.801330] usb 1-3: USB disconnect, address 7
Nov  2 18:14:01 suigintou kernel: [ 3766.964103] usb 1-3: new high speed USB device using ehci_hcd and address 8
Nov  2 18:14:16 suigintou kernel: [ 3782.076089] usb 1-3: device descriptor read/64, error -110
Nov  2 18:14:32 suigintou kernel: [ 3797.292124] usb 1-3: device descriptor read/64, error -110
Nov  2 18:14:32 suigintou kernel: [ 3797.509136] usb 1-3: new high speed USB device using ehci_hcd and address 9
Nov  2 18:14:47 suigintou kernel: [ 3812.620074] usb 1-3: device descriptor read/64, error -110
Nov  2 18:15:02 suigintou kernel: [ 3827.836502] usb 1-3: device descriptor read/64, error -110
Nov  2 18:15:02 suigintou kernel: [ 3828.052129] usb 1-3: new high speed USB device using ehci_hcd and address 10
Nov  2 18:15:07 suigintou kernel: [ 3833.072284] usb 1-3: device descriptor read/8, error -110
Nov  2 18:15:12 suigintou kernel: [ 3838.192267] usb 1-3: device descriptor read/8, error -110
Nov  2 18:15:13 suigintou kernel: [ 3838.408094] usb 1-3: new high speed USB device using ehci_hcd and address 11
Nov  2 18:15:18 suigintou kernel: [ 3843.428269] usb 1-3: device descriptor read/8, error -110
Nov  2 18:15:23 suigintou kernel: [ 3848.548245] usb 1-3: device descriptor read/8, error -110
Nov  2 18:15:23 suigintou kernel: [ 3848.652423] hub 1-0:1.0: unable to enumerate USB device on port 3
Nov  2 18:15:23 suigintou kernel: [ 3848.924074] usb 3-1: new full speed USB device using uhci_hcd and address 2
Nov  2 18:15:38 suigintou kernel: [ 3864.036094] usb 3-1: device descriptor read/64, error -110
Nov  2 18:15:54 suigintou kernel: [ 3879.252105] usb 3-1: device descriptor read/64, error -110
Nov  2 18:15:54 suigintou kernel: [ 3879.468679] usb 3-1: new full speed USB device using uhci_hcd and address 3
Nov  2 18:16:09 suigintou kernel: [ 3894.580090] usb 3-1: device descriptor read/64, error -110
Nov  2 18:16:24 suigintou kernel: [ 3909.800070] usb 3-1: device descriptor read/64, error -110
Nov  2 18:16:24 suigintou kernel: [ 3910.016064] usb 3-1: new full speed USB device using uhci_hcd and address 4
Nov  2 18:16:29 suigintou kernel: [ 3915.037176] usb 3-1: device descriptor read/8, error -110
Nov  2 18:16:34 suigintou kernel: [ 3920.157427] usb 3-1: device descriptor read/8, error -110
Nov  2 18:16:35 suigintou kernel: [ 3920.372101] usb 3-1: new full speed USB device using uhci_hcd and address 5
Nov  2 18:16:40 suigintou kernel: [ 3925.393649] usb 3-1: device descriptor read/8, error -110
Nov  2 18:16:45 suigintou kernel: [ 3930.513891] usb 3-1: device descriptor read/8, error -110
Nov  2 18:16:45 suigintou kernel: [ 3930.616094] hub 3-0:1.0: unable to enumerate USB device on port 1

```
Any idea what is going on?  I've seen a lot about USB devices not automounting in Karmic, but nothing about them mounting only to error out like this.  Again, the drive works fine in MacOSX and Windows XP, chkdsk /R shows the ntfs volume is fine, all my data is still there.

---

### Post by ibchristie on 2009-11-04
I'm looking for a solution to the same problem. I have a Seagate 1TB external drive and I am led to believe it will go into sleep mode after about 15 minutes. This is not a problem for Windows but apparently the Koala drops the connection and then reconnects as USB 1.1. It sounds like you are having a problem with sleep mode too. I have only just connected mine and came across descriptions of the problem when I was searching for information on the drive format. Before I store anything on my drive I want to know what file system it uses.

---

### Post by canas on 2009-11-04
Just cross-referencing another thread describing this problem.  Don't want to duplicate effort to fix it: [http://ubuntuforums.org/showthread.php?t=1300822](http://ubuntuforums.org/showthread.php?t=1300822)

---

### Post by Dourado on 2009-12-01
I also have a Seagate FreeAgent Xtreme. I don't have problems with the sleep mode. People seem to have figured that one out and included it in the more recent kernels. Either way, I can turn off standby mode by using: 'sdparm -6 --clear=STANDBY /dev/sd*'

The problem still persists for me after turning off the standby mode. I actually get a dropped connection in the middle of reads/writes. The drive becomes inaccessible and I have to power-cycle the drive to get it to become recognized again.

I have noticed that it works fine if you use USB 1.1 only: 'modprobe -r ehci_hcd' However, this is not a good solution because it's far too SLOW.

I have seen lots of other threads suggesting to increase/decrease max_sectors with sysfs or using udev rules and even writing a file to the disk regularly with a cron job, but nothing seems to work for this drive so far.

 Very frustrating.

---

