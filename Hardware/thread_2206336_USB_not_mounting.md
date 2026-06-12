---
title: "USB not mounting"
date: 2014-02-18
forum: Hardware
---

### Post by ggdhines on 2014-02-18
Hi, I have a Lacie usb external hard drive that I am trying to mount without success on Kubuntu 13.10. The drive works fine on a Mac. When I do lsusb, one of the following lines is
Bus 003 Device 008: ID 059f:1061 LaCie, Ltd 

So I know that the computer is seeing the drive. But when I try "sudo fdisk -l" results don't show anything for the drive and in fact the program freezes until I unplug the drive. The following is the result from dmesg. Any help is greatly appreciated

```
[  885.950070] usb 3-7: new high-speed USB device number 7 using xhci_hcd
[  885.983971] usb 3-7: New USB device found, idVendor=059f, idProduct=1061
[  885.983980] usb 3-7: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[  885.983985] usb 3-7: Product: Rugged USB3-FW
[  885.983989] usb 3-7: Manufacturer: LaCie
[  885.983992] usb 3-7: SerialNumber: 00000000f49de30e308d
[  885.984671] usb-storage 3-7:1.0: USB Mass Storage device detected
[  885.984953] scsi9 : usb-storage 3-7:1.0
[  886.984227] scsi 9:0:0:0: Direct-Access     LaCie    Rugged FW USB3   051E PQ: 0 ANSI: 6
[  886.984713] sd 9:0:0:0: Attached scsi generic sg7 type 0
[  886.993875] sd 9:0:0:0: [sdh] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  886.994393] sd 9:0:0:0: [sdh] Write Protect is off
[  886.994399] sd 9:0:0:0: [sdh] Mode Sense: 43 00 00 00
[  886.994852] sd 9:0:0:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  887.092230]  sdh: sdh1 sdh2 sdh3
[  887.094362] sd 9:0:0:0: [sdh] Attached SCSI disk
[  894.839229] usb 3-7: reset high-speed USB device number 7 using xhci_hcd
[  894.872235] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f7ffe00
[  894.872237] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021f7ffe40
[ 1069.974816] ata2: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1069.974819] ata2: irq_stat 0x00400040, connection status changed
[ 1069.974821] ata2: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1069.974824] ata2: hard resetting link
[ 1069.974830] ata1: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1069.974832] ata1: irq_stat 0x00400040, connection status changed
[ 1069.974834] ata1: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1069.974836] ata1: hard resetting link
[ 1069.974842] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1069.974845] ata5: irq_stat 0x00400040, connection status changed
[ 1069.974846] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1069.974848] ata5: hard resetting link
[ 1070.697276] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1070.697293] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1070.699025] ata1.00: configured for UDMA/133
[ 1070.699116] ata1: EH complete
[ 1070.700022] ata2.00: configured for UDMA/133
[ 1070.700277] ata2: EH complete
[ 1070.701271] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1070.704377] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[ 1070.704381] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff8802240f1118), AE_NOT_FOUND (20130517/psparse-536)
[ 1070.705187] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[ 1070.705190] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff8802240f1118), AE_NOT_FOUND (20130517/psparse-536)
[ 1070.705194] ata5.00: configured for UDMA/100
[ 1070.705911] ata5: EH complete
[ 1221.833512] ata1: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1221.833525] ata1: irq_stat 0x00400040, connection status changed
[ 1221.833527] ata1: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1221.833530] ata1: hard resetting link
[ 1221.833537] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1221.833539] ata5: irq_stat 0x00400040, connection status changed
[ 1221.833541] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1221.833543] ata5: hard resetting link
[ 1221.833550] ata2: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1221.833552] ata2: irq_stat 0x00400040, connection status changed
[ 1221.833553] ata2: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1221.833555] ata2: hard resetting link
[ 1222.556220] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1222.556236] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1222.557812] ata1.00: configured for UDMA/133
[ 1222.557904] ata1: EH complete
[ 1222.559320] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[ 1222.559324] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff8802240f1118), AE_NOT_FOUND (20130517/psparse-536)
[ 1222.560116] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[ 1222.560118] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff8802240f1118), AE_NOT_FOUND (20130517/psparse-536)
[ 1222.560123] ata5.00: configured for UDMA/100
[ 1222.560204] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1222.560848] ata5: EH complete
[ 1222.562948] ata2.00: configured for UDMA/133
[ 1222.563202] ata2: EH complete
[ 1262.149046] ata1.00: limiting speed to UDMA/100:PIO4
[ 1262.149059] ata1: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1262.149061] ata1: irq_stat 0x00400040, connection status changed
[ 1262.149062] ata1: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1262.149065] ata1: hard resetting link
[ 1262.149073] ata5.00: limiting speed to UDMA/66:PIO4
[ 1262.149076] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1262.149077] ata5: irq_stat 0x00400040, connection status changed
[ 1262.149078] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1262.149080] ata5: hard resetting link
[ 1262.149087] ata2.00: limiting speed to UDMA/100:PIO4
[ 1262.149090] ata2: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1262.149091] ata2: irq_stat 0x00400040, connection status changed
[ 1262.149093] ata2: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1262.149095] ata2: hard resetting link
[ 1262.871401] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1262.871417] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1262.871430] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1262.873027] ata1.00: configured for UDMA/100
[ 1262.873120] ata1: EH complete
[ 1262.874187] ata2.00: configured for UDMA/100
[ 1262.874485] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[ 1262.874488] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff8802240f1118), AE_NOT_FOUND (20130517/psparse-536)
[ 1262.874498] ata2: EH complete
[ 1262.875358] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[ 1262.875360] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff8802240f1118), AE_NOT_FOUND (20130517/psparse-536)
[ 1262.875364] ata5.00: configured for UDMA/66
[ 1262.875844] ata5: EH complete
[ 1365.341871] sd 9:0:0:0: [sdh] Unhandled error code
[ 1365.341874] sd 9:0:0:0: [sdh]  
[ 1365.341875] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1365.341876] sd 9:0:0:0: [sdh] CDB: 
[ 1365.341877] Read(10): 28 00 00 06 40 30 00 00 08 00
[ 1365.341882] end_request: I/O error, dev sdh, sector 409648
[ 1365.341884] Buffer I/O error on device sdh2, logical block 1
[ 1365.341886] usb 3-7: USB disconnect, device number 7
[ 1365.341916] sd 9:0:0:0: timing out command, waited 180s
[ 1365.341933] sd 9:0:0:0: [sdh] Unhandled error code
[ 1365.341934] sd 9:0:0:0: [sdh]  
[ 1365.341935] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1365.341936] sd 9:0:0:0: [sdh] CDB: 
[ 1365.341937] Read(10): 28 00 2a a7 8d 60 00 00 08 00
[ 1365.341941] end_request: I/O error, dev sdh, sector 715623776
[ 1365.341943] Buffer I/O error on device sdh3, logical block 1
[ 1365.343008] sd 9:0:0:0: [sdh] Synchronizing SCSI cache
[ 1365.343021] sd 9:0:0:0: [sdh]  
[ 1365.343022] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
```

---

### Post by ajgreeny on 2014-02-18
How is the disk formatted?  If it's hfs+ it requires that you install the hfsplus package (and maybe others) in order to mount it.

---

### Post by ggdhines on 2014-02-20
Thanks for the reply. Yes the drive is hfs+ formatted. I've tried everything I could find about getting hfs+ drives to mount (would have been happy just being able to read the drive), including turning off journaling but nothing seems to work. I tried to force the mount using the command "mount -t hfsplus" (with the hfsplus package installed). Seems simpler (but rather painful) to just copy the files on another USB stick (have to repeat, since the second stick has smaller memory). 

G.

---

### Post by Jerome____ on 2014-11-06
hello,
I'm on an other OS linux (last version and stable) and i have the same HDD than you.
I have problem with this HDD and i read somme other had same problem.
For me, impossible to mount it on USB3.0 port... the keyboard and mouse (usb connected) freeze, the sound goes on loop. When i connect it on USB2.0, it works.
SO... i try to change partitions and system files... same problem all the time.
Other HDD with hfs+ on usb3.0 works perfectly, this one, hfs+ or VFAT or NTFS was same. All i read on internet about this HDD look like no-one know what's happen and no-one resolved the issue.
Definitly, LACIE is not a good choice due to the quality and compatibility choice of this company. I had some problem with Toshiba also... not for mount, but loose all data precisely two years after buy it... no use 2 month before and take care my drives (not use too much alos...). Look like some company do some commercial choice more than quality work.

SO for me, now and for futur as long as this not change, i will only choose WD HDD, never more LACIE, never more toshiba and don't want to run risk to loose again datas because company not serious or strange commercial politic. 
I think it would be for the futur the only one chance to see company force to change this politic of low quality/compatibility. For them, we are not client, we are just customer. So... not eat this ****.

good luck and sorry.

---

### Post by Bucky Ball on 2014-11-06
13.10 is no longer supported by Canonical or these forums. Please read [HERE]("http://ubuntuforums.org/showthread.php?t=2229730") and install a supported release. Thanks.

Please post a new thread if you have any issues installing a supported releases or you still have the same issues on the new install. Good luck. 

PS: Also, please use [code] tags when posting code. See the last link in my signature for how. Neater, space-saving and easier to read.

---

