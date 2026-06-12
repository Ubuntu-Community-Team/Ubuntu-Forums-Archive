---
title: "Cannot read CD Card Karmic 32-bit"
date: 2010-01-01
forum: Hardware
---

### Post by dibblego on 2010-01-01
I have several SD cards. On both my 32-bit karmic machines, with very different hardware, I cannot read any SD card that is >= 4GB. I can see it in lsusb output (Alcor Micro Corp.) but not in fdisk output. What might be the problem?

Others seem to have the same problem
[http://ubuntuforums.org/showthread.php?t=1136196](http://ubuntuforums.org/showthread.php?t=1136196)

> 
# dmesg && fdisk -l && lsusb                        
[510668.428012] usb 1-5: new high speed USB device using ehci_hcd and address 24
[510668.565934] usb 1-5: configuration #1 chosen from 1 choice                  
[510668.566225] scsi13 : SCSI emulation for USB Mass Storage devices            
[510668.566325] usb-storage: device found at 24                                 
[510668.566328] usb-storage: waiting for device to settle before scanning       
[510673.564217] usb-storage: device scan complete                               
[510673.565825] scsi 13:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[510673.566152] sd 13:0:0:0: Attached scsi generic sg2 type 0
[510704.104025] usb 1-5: reset high speed USB device using ehci_hcd and address 24
[510714.356013] usb 1-5: reset high speed USB device using ehci_hcd and address 24
[510730.600024] usb 1-5: reset high speed USB device using ehci_hcd and address 24
[510730.852041] usb 1-5: reset high speed USB device using ehci_hcd and address 24
[510741.096013] usb 1-5: reset high speed USB device using ehci_hcd and address 24
[510741.230002] sd 13:0:0:0: Device offlined - not ready after error recovery
[510741.230039] sd 13:0:0:0: rejecting I/O to offline device
[510741.230050] sd 13:0:0:0: rejecting I/O to offline device
[510741.230055] sd 13:0:0:0: rejecting I/O to offline device
[510741.230058] sd 13:0:0:0: [sdb] READ CAPACITY failed
[510741.230060] sd 13:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[510741.230063] sd 13:0:0:0: [sdb] Sense not available.
[510741.230068] sd 13:0:0:0: rejecting I/O to offline device
[510741.230071] sd 13:0:0:0: [sdb] Write Protect is off
[510741.230073] sd 13:0:0:0: [sdb] Mode Sense: 00 00 00 00
[510741.230075] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[510741.230184] sd 13:0:0:0: [sdb] Attached SCSI removable disk

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007d92f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21986   176602513+  83  Linux
/dev/sda2           29880       30401     4192965   82  Linux swap / Solaris
/dev/sda3           21987       29879    63400522+   5  Extended
/dev/sda5           21987       29551    60765831   83  Linux
/dev/sda6           29552       29879     2634628+  82  Linux swap / Solaris

Partition table entries are not in disk order
Bus 002 Device 009: ID 046d:0a12 Logitech, Inc.
Bus 002 Device 004: ID 045e:00f9 Microsoft Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 024: ID 058f:6331 Alcor Micro Corp.
Bus 001 Device 018: ID 05ac:1292 Apple, Inc. iPhone 3G
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

