---
title: "Acomdata IDE/SATA enclosure not working"
date: 2008-05-30
forum: Hardware
---

### Post by superwad on 2008-05-30
I just got a new hard drive enclosure.  It's an Acomdata IDE/SATA hybrid enclosure.  Right now I have a 320GB SATA2 drive installed.  It's been formatted NTFS.  Plug it into a Windows XP machine, and it detects and is available for use.  Plug it into a fresh Kubuntu 8.04 install, and it doesn't detect.

I get this output in dmesg though:

```
[105469.446073] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[105469.558265] usb 5-4: device descriptor read/64, error -71
[105469.775149] usb 5-4: device descriptor read/64, error -71
[105469.991024] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[105470.101969] usb 5-4: device descriptor read/64, error -71
[105470.317842] usb 5-4: device descriptor read/64, error -71
[105470.533719] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[105470.941481] usb 5-4: device not accepting address 3, error -71
[105471.053428] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[105471.461204] usb 5-4: device not accepting address 3, error -71
[105471.461257] scsi 8:0:0:0: Device offlined - not ready after error recovery
[105471.461306] usb 5-4: USB disconnect, address 3
[105471.573189] usb 5-4: new high speed USB device using ehci_hcd and address 4
[105471.685073] usb 5-4: device descriptor read/64, error -71
[105471.904967] usb 5-4: device descriptor read/64, error -71
[105472.117150] usb 5-4: new high speed USB device using ehci_hcd and address 5
[105472.229783] usb 5-4: device descriptor read/64, error -71
[105472.445685] usb 5-4: device descriptor read/64, error -71
[105472.661547] usb 5-4: new high speed USB device using ehci_hcd and address 6
[105473.068309] usb 5-4: device not accepting address 6, error -71
[105473.180250] usb 5-4: new high speed USB device using ehci_hcd and address 7
[105473.588995] usb 5-4: device not accepting address 7, error -71
[105566.830570] UDF-fs: No VRS found
[105566.873692] ISO 9660 Extensions: Microsoft Joliet Level 3
[105566.875185] ISO 9660 Extensions: RRIP_1991A
```

I'm not quite sure what to do here.  Any help is appreciated.

Thanks

---

### Post by superwad on 2008-06-03
I've managed to do a little bit more work on this problem.  From what I can gather, I only have a problem reading the drive in Kubuntu if there is a SATA drive in the enclosure.  If it is IDE, the drive works just fine.

On Windows XP SP2:
 - IDE: works
 - SATA: works

On Kubuntu:
 - IDE: works
 - SATA: errors as in first post

I've tried it with only one SATA drive, but with 5 IDE drives ranging in capacity from 1.2GB to 40GB, and all work in Kubuntu (except one that was dead, but that's understandable).

Any thoughts out there?

---

### Post by superwad on 2008-06-05
Shameless bump.  No new progress on this situation.  Any other insights?

---

### Post by Mais on 2008-06-18
I'm having similar issues with an Acom IDE/SATA enclosure. However, neither IDE nor SATA drives are working.

dmesg output:[INDENT][I][  636.901181] usb 3-1: new high speed USB device using ehci_hcd and address 7
[  636.964573] usb 3-1: configuration #1 chosen from 1 choice
[  636.965136] scsi4 : SCSI emulation for USB Mass Storage devices
[  636.965397] usb-storage: device found at 7
[  636.965400] usb-storage: waiting for device to settle before scanning
[  639.963051] usb-storage: device scan complete
[  641.866825] scsi 4:0:0:0: Direct-Access     ST312002 6A                    PQ: 0 ANSI: 2 CCS
[  641.867855] sd 4:0:0:0: [sda] 234375000 512-byte hardware sectors (120000 MB)
[  641.868232] sd 4:0:0:0: [sda] Write Protect is off
[  641.868236] sd 4:0:0:0: [sda] Mode Sense: 00 38 00 00
[  641.868239] sd 4:0:0:0: [sda] Assuming drive cache: write through
[  641.868939] sd 4:0:0:0: [sda] 234375000 512-byte hardware sectors (120000 MB)
[  641.869361] sd 4:0:0:0: [sda] Write Protect is off
[  641.869366] sd 4:0:0:0: [sda] Mode Sense: 00 38 00 00
[  641.869369] sd 4:0:0:0: [sda] Assuming drive cache: write through
[  641.869376]  sda:<6>usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  662.031480] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  680.467894] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  685.597868] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  703.709301] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  708.823008] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  726.938276] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  729.221215] atkbd.c: Unknown key pressed (translated set 2, code 0xb4 on isa0060/serio0).
[  729.221223] atkbd.c: Use 'setkeycodes e034 <keycode>' to make it known.
[  729.282983] atkbd.c: Unknown key released (translated set 2, code 0xb4 on isa0060/serio0).
[  729.282991] atkbd.c: Use 'setkeycodes e034 <keycode>' to make it known.
[  732.060174] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  750.175382] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  755.295294] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  773.408511] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  778.534957] usb 3-1: reset high speed USB device using ehci_hcd and address 7
[  781.600575] sd 4:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  781.600589] end_request: I/O error, dev sda, sector 0
[  781.600592] printk: 5 messages suppressed.
[  781.600595] Buffer I/O error on device sda, logical block 0
[/I][/INDENT]lsusb output:
[INDENT] Bus 003 Device 007: ID 0c0b:b157 Dura Micro, Inc. (Acomdata) 
[/INDENT]Apparently there are a lot of issues with enclosures not working well with Linux in USB2.0. It would be ridiculous to try and use USB1.0 for some of the data transfer I do. If I figure this out, I will let you know. Hopefully someone else may have some tips for the both of us.

---

