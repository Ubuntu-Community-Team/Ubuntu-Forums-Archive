---
title: "Can't mount old IDE hard drive on USB/ATAPI interface"
date: 2014-05-13
forum: Hardware
---

### Post by ramsey-hazbun on 2014-05-13
I have a 1.2GB HDD (Western Digital Caviar 11200 circa Aug 1997) that I'm worried might be failing.  The tool it was in has been without power for over 2-3 years.  I replaced the motherboard battery and was able to get the computer to recognize the drive and start booting.  The first time through it hanged while starting Windows 3.11.  Now it hangs immediately after POST, with the classic "Non system disk.  Abort, Retry, or Fail?"

The tool it is in has been maintained by graduate students for about 20 years.  Suffice to say I inherited the system in a fairly sad state, and there is no backup.  The control software on the computer is more or less irreplaceable.

I have removed the HDD from the old computer (a 486) and tried to connect it to my desktop using a USB/ATAPI bridge.  Drive is set to Master.  In both Windows 7 and Ubuntu 12.04 I am unable to mount the drive.  Based on the output below, the hardware/firmware seems to be recognized but there isn't a valid partition table to load.

Below is a bunch of useful errors and diagnostics.  From my understanding it seems, at best, the hard drive has a corrupt partition table.  But the fact that parted and fdisk don't seem to see the drive suggests something else might be going on.  The fact that it seems to be having I/O errors on the first sector is not very encouraging.  Does anyone have a clue what it might be?  The drive is very old, so it's possible it failed, but I'm hoping I can rescue something.  Perhaps there is a kernel/driver/settings issues I missed for these old drives or the USB/ATAPI bridge?  I am going to take another crack at mounting the drive in Windows since I've been reading about some issues with the USB/ATAPI bridges in Ubuntu.

fdisk -l does not list the drive

I get the following error when running parted /dev/sdg:
> Error: Error opening /dev/sdg: No such device or address

lsusb

> Bus 002 Device 080: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge


dmesg
> [ 2300.245168] usb 2-1.6: new high-speed USB device number 80 using ehci_hcd
[ 2300.339271] scsi12 : usb-storage 2-1.6:1.0
[ 2301.335074] scsi 12:0:0:0: Direct-Access     WDC AC11 200L                  PQ: 0 ANSI: 2 CCS
[ 2301.336594] sd 12:0:0:0: Attached scsi generic sg7 type 0
[ 2301.337094] sd 12:0:0:0: [sdg] 2503872 512-byte logical blocks: (1.28 GB/1.19 GiB)
[ 2301.337830] sd 12:0:0:0: [sdg] Write Protect is off
[ 2301.337838] sd 12:0:0:0: [sdg] Mode Sense: 28 00 00 00
[ 2301.339990] sd 12:0:0:0: [sdg] No Caching mode page found
[ 2301.339998] sd 12:0:0:0: [sdg] Assuming drive cache: write through
[ 2301.342490] sd 12:0:0:0: [sdg] No Caching mode page found
[ 2301.342496] sd 12:0:0:0: [sdg] Assuming drive cache: write through
[ 2331.598262] usb 2-1.6: reset high-speed USB device number 80 using ehci_hcd
[ 2341.738078] usb 2-1.6: reset high-speed USB device number 80 using ehci_hcd
[ 2358.431779] usb 2-1.6: reset high-speed USB device number 80 using ehci_hcd
[ 2358.599281] usb 2-1.6: reset high-speed USB device number 80 using ehci_hcd
[ 2368.735213] usb 2-1.6: reset high-speed USB device number 80 using ehci_hcd
[ 2368.827468] sd 12:0:0:0: Device offlined - not ready after error recovery
[ 2368.827481] sd 12:0:0:0: [sdg] Unhandled error code
[ 2368.827485] sd 12:0:0:0: [sdg]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 2368.827490] sd 12:0:0:0: [sdg] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 2368.827503] end_request: I/O error, dev sdg, sector 0
[ 2368.827509] Buffer I/O error on device sdg, logical block 0
[ 2368.827561] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827594] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827614] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827634] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827641] ldm_validate_partition_table(): Disk read failed.
[ 2368.827651] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827665] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827678] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827691] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827699] Dev sdg: unable to read RDB block 0
[ 2368.827708] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827721] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827748] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827758] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827770] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827784] sd 12:0:0:0: rejecting I/O to offline device
[ 2368.827791]  sdg: unable to read partition table
[ 2368.827975] sd 12:0:0:0: [sdg] Attached SCSI disk


---

