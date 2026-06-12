---
title: "external hard drive unmounts and does not remount"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by oddchild on 2008-03-20
I recently bought a very nice 600 gig USB harddrive. The problem is, it keeps unmounting itself. I cannot plug it back in while I am running ubuntu - I have to restart each time. 

In puppy linux, if I plug it in while the system is running it detects and works fine, without unmounting itself.. however, with ubuntu it unmounts and will not let me put it back on until i restart the computer. 

here is the dmesg
```

[ 3472.800000] end_request: I/O error, dev sdb, sector 319150152
[ 3472.800000] Buffer I/O error on device sdb1, logical block 39893513
[ 3472.800000] Buffer I/O error on device sdb1, logical block 39893514
[ 3472.800000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3472.800000] Buffer I/O error on device sdb1, logical block 39893512
[ 3472.876000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3472.876000] Buffer I/O error on device sdb1, logical block 786433
[ 3472.876000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3472.876000] Buffer I/O error on device sdb1, logical block 786433
[ 3472.880000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3472.880000] Buffer I/O error on device sdb1, logical block 786433
[ 3472.880000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3472.880000] Buffer I/O error on device sdb1, logical block 786433
[ 3472.908000] usb 1-6: new high speed USB device using ehci_hcd and address 3
[ 3472.916000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3472.916000] Buffer I/O error on device sdb1, logical block 786433
[ 3472.916000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3472.916000] Buffer I/O error on device sdb1, logical block 786433
[ 3472.916000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3472.916000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3473.000000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3473.024000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3473.068000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3473.260000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3473.300000] scsi 0:0:0:0: rejecting I/O to dead device
[ 3488.452000] usb 1-6: device not accepting address 3, error -110
[ 3488.564000] usb 1-6: new high speed USB device using ehci_hcd and address 4
[ 3504.108000] usb 1-6: device not accepting address 4, error -110
[ 3504.220000] usb 1-6: new high speed USB device using ehci_hcd and address 5
[ 3514.644000] usb 1-6: device not accepting address 5, error -110
[ 3514.756000] usb 1-6: new high speed USB device using ehci_hcd and address 6
[ 3525.180000] usb 1-6: device not accepting address 6, error -110

```

and here is the sudo fdisk -l results


```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce5973cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7868    63197184    7  HPFS/NTFS
/dev/sda2           13977       14593     4956052+   5  Extended
/dev/sda3            7869       13976    49062510   83  Linux
/dev/sda5           14243       14593     2819376   82  Linux swap / Solaris
/dev/sda6           13977       14242     2136582   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I have tried mount -a etc,,, I couldn't figure it out...

I hope I provided enough information, thank you all for your help.

---

