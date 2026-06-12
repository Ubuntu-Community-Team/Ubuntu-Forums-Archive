---
title: "Mouse stops working when I use keyboard"
date: 2009-02-26
forum: Hardware
---

### Post by aws910 on 2009-02-26
Usb mouse.  Title pretty much says it all - mouse function returns once I stop using the keyboard.  Also, when I have a usb drive connected, if I use the keyboard at all, the usb drive will be instantly disconnected, then momentarily reconnected.  Very annoying.  Recent install, intrepid ibex, running on a Lenovo 3000 N100 0768 E7U.

uncut dmesg:
```
[108290.983112] scsi 4:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[108290.995277] sd 4:0:0:0: [sdb] 31116288 512-byte hardware sectors (15932 MB)
[108290.998714] sd 4:0:0:0: [sdb] Write Protect is off
[108290.998726] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[108290.998732] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[108291.032173] sd 4:0:0:0: [sdb] 31116288 512-byte hardware sectors (15932 MB)
[108291.034631] sd 4:0:0:0: [sdb] Write Protect is off
[108291.034643] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[108291.034648] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[108291.034658]  sdb: sdb1
[108291.040443] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[108291.040635] sd 4:0:0:0: Attached scsi generic sg2 type 0
[108314.241044] usb 5-5: USB disconnect, address 103
[108314.241768] __ratelimit: 58 callbacks suppressed
[108314.241775] Buffer I/O error on device sdb1, logical block 1
[108314.241781] lost page write due to I/O error on sdb1
[108314.267584] scsi 4:0:0:0: rejecting I/O to dead device
[108314.596397] hub 5-0:1.0: unable to enumerate USB device on port 5
[108314.596444] usb 2-1: USB disconnect, address 106
[108315.232170] usb 5-5: new high speed USB device using ehci_hcd and address 106
[108315.388943] usb 5-5: configuration #1 chosen from 1 choice
[108315.397061] scsi5 : SCSI emulation for USB Mass Storage devices
[108315.399435] usb-storage: device found at 106
[108315.399446] usb-storage: waiting for device to settle before scanning
[108315.636152] usb 2-1: new low speed USB device using uhci_hcd and address 107
[108315.814464] usb 2-1: configuration #1 chosen from 1 choice
[108315.836707] input: Razer Razer Diamondback Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input935
[108315.873431] input,hidraw0: USB HID v1.10 Mouse [Razer Razer Diamondback Optical Mouse] on usb-0000:00:1d.1-1
[108320.398489] usb-storage: device scan complete
[108320.400485] scsi 5:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[108320.413533] sd 5:0:0:0: [sdb] 31116288 512-byte hardware sectors (15932 MB)
[108320.416543] sd 5:0:0:0: [sdb] Write Protect is off
[108320.416555] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[108320.416561] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[108320.430717] sd 5:0:0:0: [sdb] 31116288 512-byte hardware sectors (15932 MB)
[108320.435646] sd 5:0:0:0: [sdb] Write Protect is off
[108320.435657] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[108320.435662] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[108320.440017]  sdb: sdb1
[108320.446988] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[108320.449507] sd 5:0:0:0: Attached scsi generic sg2 type 0
[108331.832671] usb 5-5: USB disconnect, address 106
[108331.836356] Buffer I/O error on device sdb1, logical block 1
[108331.836369] lost page write due to I/O error on sdb1
[108331.876454] scsi 5:0:0:0: rejecting I/O to dead device
[108332.148163] usb 5-5: new high speed USB device using ehci_hcd and address 107
[108332.300527] usb 5-5: configuration #1 chosen from 1 choice
[108332.308359] scsi6 : SCSI emulation for USB Mass Storage devices
[108332.309909] usb-storage: device found at 107
[108332.309914] usb-storage: waiting for device to settle before scanning
[108332.505110] usb 5-5: USB disconnect, address 107
[108332.748440] usb 5-5: new high speed USB device using ehci_hcd and address 109
[108332.941434] usb 5-5: configuration #1 chosen from 1 choice
[108332.968542] scsi7 : SCSI emulation for USB Mass Storage devices
[108332.969454] usb-storage: device found at 109
[108332.969460] usb-storage: waiting for device to settle before scanning
[108333.148155] usb 2-1: reset low speed USB device using uhci_hcd and address 107
[108337.970676] usb-storage: device scan complete
[108337.972589] scsi 7:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[108337.979904] sd 7:0:0:0: [sdb] 31116288 512-byte hardware sectors (15932 MB)
[108337.983902] sd 7:0:0:0: [sdb] Write Protect is off
[108337.983914] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[108337.983920] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[108338.013544] sd 7:0:0:0: [sdb] 31116288 512-byte hardware sectors (15932 MB)
[108338.017076] sd 7:0:0:0: [sdb] Write Protect is off
[108338.017089] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[108338.017094] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[108338.017104]  sdb: sdb1
[108338.022381] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[108338.022570] sd 7:0:0:0: Attached scsi generic sg2 type 0
[108355.798252] usb 5-5: USB disconnect, address 109
[108355.800521] Buffer I/O error on device sdb1, logical block 1
[108355.800535] lost page write due to I/O error on sdb1
[108355.828375] scsi 7:0:0:0: rejecting I/O to dead device
[108356.117319] usb 5-5: new high speed USB device using ehci_hcd and address 110
[108356.270828] usb 5-5: configuration #1 chosen from 1 choice
[108356.271985] scsi8 : SCSI emulation for USB Mass Storage devices
[108356.272934] usb-storage: device found at 110
[108356.272949] usb-storage: waiting for device to settle before scanning
[108356.274069] usb 2-1: USB disconnect, address 107
[108357.064066] usb 2-1: new low speed USB device using uhci_hcd and address 108
[108357.243497] usb 2-1: configuration #1 chosen from 1 choice
[108357.269615] input: Razer Razer Diamondback Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input936
[108357.309223] input,hidraw0: USB HID v1.10 Mouse [Razer Razer Diamondback Optical Mouse] on usb-0000:00:1d.1-1
[108358.257568] usb 5-5: USB disconnect, address 110

```

The "Android phone" is my G1 - I have no trouble mounting/using it as a mass storage device on any other computer, regardless of OS.

Thanks in advance for any assistance anyone can give me!

---

