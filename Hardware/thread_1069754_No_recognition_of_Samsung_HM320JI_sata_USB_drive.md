---
title: "No recognition of Samsung HM320JI sata USB drive"
date: 2009-02-14
forum: Hardware
---

### Post by Harriak on 2009-02-14
Hi,

I bought a new Samsung HM320JI sata USB drive, but it is not recognized (rather) accepted) by Ubuntu 8.4 because  it is NTFS formatted.
(It is recognized by Win XP).

Advice of the Ubuntu system is to mount it at my own risk : mount -t ntfs-3g /dev/sdc5 /media/disk -o force

Anyone can tell me what's the risk to my system of inserting this line trhough the Terminal?

cheers Harriak

---

### Post by halfmanhalfbug on 2009-02-14
Hi Harriak
Ubuntu 8.04 and 8.10 should be able to automagically mount a drive formatted with ntfs. I too have been having trouble with an external sata usb drive but the problem is the ehci_hcd module which runs usb 2.0. Check your error messages immediately after plugging in the drive:
```
dmesg | tail -50
```
Mine look like this:
```
Feb  1 04:30:29 crash kernel: [  209.347086] usb 3-1: new high speed USB device using ehci_hcd and address 3
Feb  1 04:30:29 crash kernel: [  209.415006] usb 3-1: configuration #1 chosen from 1 choice
Feb  1 04:30:30 crash kernel: [  209.499978] usbcore: registered new interface driver libusual
Feb  1 04:30:30 crash kernel: [  209.528782] Initializing USB Mass Storage driver...
Feb  1 04:30:30 crash kernel: [  209.533355] scsi2 : SCSI emulation for USB Mass Storage devices
Feb  1 04:30:30 crash kernel: [  209.537029] usbcore: registered new interface driver usb-storage
Feb  1 04:30:30 crash kernel: [  209.537214] USB Mass Storage support registered.
Feb  1 04:30:35 crash kernel: [  212.199623] scsi 2:0:0:0: Direct-Access     ST925082 7AS                   PQ: 0 ANSI: 2
Feb  1 04:30:35 crash kernel: [  212.207368] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Feb  1 04:30:35 crash kernel: [  212.209994] sd 2:0:0:0: [sdb] Write Protect is off
Feb  1 04:30:35 crash kernel: [  212.211595] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Feb  1 04:30:35 crash kernel: [  212.214233] sd 2:0:0:0: [sdb] Write Protect is off
Feb  1 04:30:35 crash kernel: [  212.214242]  sdb:<6>usb 3-1: reset high speed USB device using ehci_hcd and address 3
Feb  1 04:30:35 crash kernel: [  212.579531] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Feb  1 04:30:35 crash kernel: [  212.823440] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Feb  1 04:30:36 crash kernel: [  213.067315] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Feb  1 04:30:36 crash kernel: [  213.311216] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Feb  1 04:30:36 crash kernel: [  213.555129] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Feb  1 04:30:36 crash kernel: [  213.688020] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Feb  1 04:30:36 crash kernel: [  213.688028] end_request: I/O error, dev sdb, sector 0
Feb  1 04:30:36 crash kernel: [  213.811016] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Feb  1 04:30:37 crash kernel: [  214.066916] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Feb  1 04:30:37 crash kernel: [  214.318811] usb 3-1: reset high speed USB device using ehci_hcd and address 3
```
If you have a similar messages you can disconnect your hard-drive and remove the ehci_hcd module from the kernel:
```
sudo modprobe -r ehci_hcd
```
Plug in your hard-drive again. It will be mounted as usb 1.0 rather than usb 2.0. If it mounts OK then the ehci_hcd module is the problem. I have googled "ehci_hcd" and found a mountain of bug reports but no fix in sight. Sigh.
Good luck
hmhb

---

### Post by neshma on 2009-07-09
I also have the same drive. Tried almost everything and it's still not working. I did the 
dmesg | tail -50thing and these are the errors that popped up. 

```
[12054.854660]  sdb: sdb1
[12055.296968] sd 7:0:0:0: [sdb] Attached SCSI disk
[12055.297060] sd 7:0:0:0: Attached scsi generic sg2 type 0
[12073.816045] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[12073.816060] Info fld=0x0
[12073.816064] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[12088.714508] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[12088.714523] Info fld=0x0
[12088.714527] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[12106.932176] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[12106.932191] Info fld=0x0
[12106.932195] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[12124.708817] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12124.708831] sd 7:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12124.708842] Info fld=0x0
[12124.708846] sd 7:0:0:0: [sdb] Add. Sense: Id CRC or ECC error
[12124.708857] end_request: I/O error, dev sdb, sector 336
[12124.708868] __ratelimit: 8 callbacks suppressed
[12124.708875] Buffer I/O error on device sdb, logical block 42
[12124.708884] Buffer I/O error on device sdb, logical block 43
[12124.708892] Buffer I/O error on device sdb, logical block 44
[12124.708899] Buffer I/O error on device sdb, logical block 45
[12124.708907] Buffer I/O error on device sdb, logical block 46
[12124.708914] Buffer I/O error on device sdb, logical block 47
[12124.708921] Buffer I/O error on device sdb, logical block 48
[12124.708928] Buffer I/O error on device sdb, logical block 49
[12124.708935] Buffer I/O error on device sdb, logical block 50
[12124.708943] Buffer I/O error on device sdb, logical block 51
[12142.639961] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12142.639974] sd 7:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12142.639986] Info fld=0x0
[12142.639994] sd 7:0:0:0: [sdb] Add. Sense: Id CRC or ECC error
[12142.640028] end_request: I/O error, dev sdb, sector 159
[12142.640039] __ratelimit: 8 callbacks suppressed
[12142.640046] Buffer I/O error on device sdb1, logical block 48
[12142.640056] Buffer I/O error on device sdb1, logical block 49
[12142.640064] Buffer I/O error on device sdb1, logical block 50
[12142.640071] Buffer I/O error on device sdb1, logical block 51
[12142.640085] Buffer I/O error on device sdb1, logical block 52
[12142.640092] Buffer I/O error on device sdb1, logical block 53
[12142.640099] Buffer I/O error on device sdb1, logical block 54
[12142.640107] Buffer I/O error on device sdb1, logical block 55
[12142.640114] Buffer I/O error on device sdb1, logical block 56
[12142.640122] Buffer I/O error on device sdb1, logical block 57
[13562.720409] usb 1-4: USB disconnect, address 7
[13594.096053] usb 1-4: new high speed USB device using ehci_hcd and address 8
[13594.229874] usb 1-4: configuration #1 chosen from 1 choice
[13594.243511] scsi8 : SCSI emulation for USB Mass Storage devices
[13594.244661] usb-storage: device found at 8
[13594.244664] usb-storage: waiting for device to settle before scanning
```

My Ubuntu version is the 9:04. What's going on here?

---

