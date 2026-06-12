---
title: "Unable to read RDB block 0 - endless loop of failing to mount external usb / ssd"
date: 2015-01-23
forum: Hardware
---

### Post by streetster on 2015-01-23
Hi Guys,

Long story short, my old laptop died a death, replaced it with a SP3. Decided I wanted to salvage what data I could off the mSATA drive. Ordered a mSATA-USB adaptor off eBay.

Adaptor arrived, I tried with an old 128gb mSATA drive in case the thing went up in smoke. No smoke but the device kept disconnecting after ~30 seconds... wondered whether it was my SP3 (or Windows 8, or USB3 or whatever). Seemed to work OK on a guy's machine at work (xp, usb2.0), so I got home, popped the 256gb mSATA drive in. Alas same 30 second disconnect...

In this 30 seconds I was able to pull a few files off... but then the drive start disconnecting&reconnecting every 2 seconds. Windows had failed me, so time to switch to Linux.

Here's the output of dmesg (unfortunately all I have managed to do is stick a live version of 14.10 on a microSD card and boot that... this means I'm stuck with onscreen keyboard to write stuff (so I'm back in Windows writing this!).

```
[  322.194730] sd 13:0:0:0: [sdc] Unhandled error code[  322.194739] sd 13:0:0:0: [sdc]  
[  322.194743] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  322.194747] sd 13:0:0:0: [sdc] CDB: 
[  322.194749] Read(10): 28 00 00 00 00 01 00 00 01 00
[  322.194763] end_request: I/O error, dev sdc, sector 1
[  322.194770] Buffer I/O error on device sdc, logical block 1
[  322.194803] sd 13:0:0:0: [sdc] Unhandled error code
[  322.194806] sd 13:0:0:0: [sdc]  
[  322.194808] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  322.194811] sd 13:0:0:0: [sdc] CDB: 
[  322.194813] Read(10): 28 00 00 00 00 02 00 00 01 00
[  322.194824] end_request: I/O error, dev sdc, sector 2
[  322.194827] Buffer I/O error on device sdc, logical block 2
[  322.195076] ldm_validate_partition_table(): Disk read failed.
[  322.195175] Dev sdc: unable to read RDB block 0
[  322.195296]  sdc: unable to read partition table
[  322.198739] sd 13:0:0:0: [sdc] READ CAPACITY failed
[  322.198749] sd 13:0:0:0: [sdc]  
[  322.198755] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  322.198760] sd 13:0:0:0: [sdc] Sense not available.
[  322.198804] sd 13:0:0:0: [sdc] Attached SCSI disk
[  322.439317] usb 2-1: new SuperSpeed USB device number 13 using xhci_hcd
[  322.456528] usb 2-1: New USB device found, idVendor=13fd, idProduct=3940
[  322.456534] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  322.456537] usb 2-1: Product: INIC-3609       
[  322.456539] usb 2-1: Manufacturer: Initio  
[  322.456541] usb 2-1: SerialNumber: 50303233313331323031373120202020
[  322.457174] usb-storage 2-1:1.0: USB Mass Storage device detected
[  322.457379] scsi14 : usb-storage 2-1:1.0
[  323.456631] scsi 14:0:0:0: Direct-Access     Initio   INIC-3609        0216 PQ: 0 ANSI: 6
[  323.456933] sd 14:0:0:0: Attached scsi generic sg2 type 0
[  323.457124] sd 14:0:0:0: [sdc] 500118191 512-byte logical blocks: (256 GB/238 GiB)
[  323.458064] sd 14:0:0:0: [sdc] Write Protect is off
[  323.458067] sd 14:0:0:0: [sdc] Mode Sense: 1f 00 10 08
[  323.458678] sd 14:0:0:0: [sdc] Write cache: disabled, read cache: enabled, supports DPO and FUA
[  324.613787] usb 2-1: USB disconnect, device number 13
```

This continues over and over until I pull the drive. Main gist seems to be that it fails to read the allocation table, and dies, then tries again. I'm wondering if there is a less intrusive way of going about this, so that I can dd the partition over to an external harddrive and then work on extracting the files I want that way.

sudo fdisk -l takes a while to run but doesnt show dev/sdc. I can give gparted a go, but I think it will fail due to the fact that Ubuntu seems to be kicking the device off when it fails.

Any help would be greatly appreciated.

---

