---
title: "External USB drive won't mount"
date: 2009-09-13
forum: Hardware
---

### Post by GrrrArrgh on 2009-09-13
Hi. I've got two usb hard drives on my computer right now. One of them I can see and access fine without any problems, the other is not cooperating. It's an issue I've been trying to fix for a few days now, and someone suggested using ubuntu as a potential solution(my primary os is windows xp). I can see an icon for the drive I want to get into, but it won't let me mount it. I was going to try doing it manually as suggested on some other forums, but don't know if that's going to work. This is what dmesg gives me:

    [  168.080016] usb 1-3: new high speed USB device using ehci_hcd and address 6
[  168.212978] usb 1-3: configuration #1 chosen from 1 choice
[  168.264140] scsi3 : SCSI emulation for USB Mass Storage devices
[  168.266162] usb-storage: device found at 6
[  168.266166] usb-storage: waiting for device to settle before scanning
[  173.264178] usb-storage: device scan complete
[  173.264658] scsi 3:0:0:0: Direct-Access     WDC      WD1600BB-00HRA0  15.0 PQ: 0 ANSI: 2
[  173.267154] sd 3:0:0:0: [sdd] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[  173.267887] sd 3:0:0:0: [sdd] Write Protect is off
[  173.267891] sd 3:0:0:0: [sdd] Mode Sense: 53 00 00 08
[  173.267895] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[  173.310158] sd 3:0:0:0: [sdd] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[  173.310973] sd 3:0:0:0: [sdd] Write Protect is off
[  173.310977] sd 3:0:0:0: [sdd] Mode Sense: 53 00 00 08
[  173.310981] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[  173.310990]  sdd:<6>sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  173.314140] sd 3:0:0:0: [sdd] Sense Key : Medium Error [current] 
[  173.314148] sd 3:0:0:0: [sdd] Add. Sense: Unrecovered read error
[  173.314155] end_request: I/O error, dev sdd, sector 0
[  173.314161] Buffer I/O error on device sdd, logical block 0
[  173.317090] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  173.317096] sd 3:0:0:0: [sdd] Sense Key : Medium Error [current] 
[  173.317101] sd 3:0:0:0: [sdd] Add. Sense: Unrecovered read error
[  173.317107] end_request: I/O error, dev sdd, sector 0
[  173.317111] Buffer I/O error on device sdd, logical block 0
[  173.319114] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  173.319119] sd 3:0:0:0: [sdd] Sense Key : Medium Error [current] 
[  173.319124] sd 3:0:0:0: [sdd] Add. Sense: Unrecovered read error
[  173.319129] end_request: I/O error, dev sdd, sector 0
[  173.319133] Buffer I/O error on device sdd, logical block 0
[  173.322619] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  173.322624] sd 3:0:0:0: [sdd] Sense Key : Medium Error [current] 
[  173.322629] sd 3:0:0:0: [sdd] Add. Sense: Unrecovered read error
[  173.322635] end_request: I/O error, dev sdd, sector 0
[  173.322638] Buffer I/O error on device sdd, logical block 0
[  173.325493] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  173.325498] sd 3:0:0:0: [sdd] Sense Key : Medium Error [current] 
[  173.325503] sd 3:0:0:0: [sdd] Add. Sense: Unrecovered read error
[  173.325509] end_request: I/O error, dev sdd, sector 0
[  173.325513] Buffer I/O error on device sdd, logical block 0
[  173.325527] ldm_validate_partition_table(): Disk read failed.
[  173.327487] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  173.327492] sd 3:0:0:0: [sdd] Sense Key : Medium Error [current] 
[  173.327497] sd 3:0:0:0: [sdd] Add. Sense: Unrecovered read error
[  173.327502] end_request: I/O error, dev sdd, sector 0
[  173.327505] Buffer I/O error on device sdd, logical block 0
[  173.330741] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  173.330747] sd 3:0:0:0: [sdd] Sense Key : Medium Error [current] 
[  173.330751] sd 3:0:0:0: [sdd] Add. Sense: Unrecovered read error
[  173.330757] end_request: I/O error, dev sdd, sector 0
[  173.330760] Buffer I/O error on device sdd, logical block 0
[  173.333616] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  173.333621] sd 3:0:0:0: [sdd] Sense Key : Medium Error [current] 
[  173.333626] sd 3:0:0:0: [sdd] Add. Sense: Unrecovered read error
[  173.333632] end_request: I/O error, dev sdd, sector 0
[  173.333635] Buffer I/O error on device sdd, logical block 0
[  173.335611] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  173.335616] sd 3:0:0:0: [sdd] Sense Key : Medium Error [current] 
[  173.335620] sd 3:0:0:0: [sdd] Add. Sense: Unrecovered read error
[  173.335626] end_request: I/O error, dev sdd, sector 0
[  173.335629] Buffer I/O error on device sdd, logical block 0
[  173.335641] Dev sdd: unable to read RDB block 0
[  173.346989] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  173.346994] sd 3:0:0:0: [sdd] Sense Key : Medium Error [current] 
[  173.346999] sd 3:0:0:0: [sdd] Add. Sense: Unrecovered read error
[  173.347005] end_request: I/O error, dev sdd, sector 0
[  177.156015] usb 5-2: new low speed USB device using uhci_hcd and address 3
[  177.331080] usb 5-2: configuration #1 chosen from 1 choice
[  177.371287] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input8
[  177.388524] generic-usb 0003:046D:C506.0002: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-2/input0
[  203.928026] usb 1-3: reset high speed USB device using ehci_hcd and address 6
[  214.172021] usb 1-3: reset high speed USB device using ehci_hcd and address 6
[  219.416019] usb 1-3: reset high speed USB device using ehci_hcd and address 6
[  229.660031] usb 1-3: reset high speed USB device using ehci_hcd and address 6
[  229.792648] sd 3:0:0:0: Device offlined - not ready after error recovery
[  229.792664] sd 3:0:0:0: [sdd] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  229.792670] end_request: I/O error, dev sdd, sector 0
[  229.792676] __ratelimit: 1 callbacks suppressed
[  229.792680] Buffer I/O error on device sdd, logical block 0
[  229.792746] sd 3:0:0:0: rejecting I/O to offline device
[  229.792751] Buffer I/O error on device sdd, logical block 3
[  229.792766] sd 3:0:0:0: rejecting I/O to offline device
[  229.792771] Buffer I/O error on device sdd, logical block 3
[  229.792784] sd 3:0:0:0: rejecting I/O to offline device
[  229.792788] Buffer I/O error on device sdd, logical block 0
[  229.792799] sd 3:0:0:0: rejecting I/O to offline device
[  229.792803] Buffer I/O error on device sdd, logical block 0
[  229.792809]  unable to read partition table
[  229.798785] sd 3:0:0:0: [sdd] Attached SCSI disk
[  229.799129] sd 3:0:0:0: Attached scsi generic sg5 type 0






So I'm not quite sure what to do next. If it's coming up with errors will it let me mount it at all? I really want the files on that drive, I just can't figure out how to gain access to them or if they're even still there. Any help would be greatly appreciated.

---

### Post by Bucky Ball on 2009-09-13
Possibly it wasn't correctly unmounted when shutting down Windows? Not an immediate fix but possible clue for you research.

If USB devices or Windows itself is not shut down properly they remain open and problematic (can be).

---

