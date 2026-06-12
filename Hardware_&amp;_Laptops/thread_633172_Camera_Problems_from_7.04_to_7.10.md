---
title: "Camera Problems from 7.04 to 7.10"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by Starcraftmazter on 2007-12-06
Hello.

My digital camera has 3 transfer modes. PC (mass storage), PictBridge (propriety), and PC Cam.

Now, in 7.04, only mass storage worked, which was great.
Since 7.10, PictBridge now works, and you get a nice popup windows with loading drivers and importing....however it can't handle recorded videos - doesn't even detect them.

The problem is, now the mass storage mode doesn't work! I When I go to mount the camera, it says, "Unable to mount Media", "There is probably no media in the drive." - but it worked fine under 7.04.

Here is the message log from when I plug it in.

> Dec  7 01:14:34 moocow kernel: [14303.282116] usb 3-1: new full speed USB device using uhci_hcd and address 6
Dec  7 01:14:34 moocow kernel: [14303.450006] usb 3-1: configuration #1 chosen from 1 choice
Dec  7 01:14:34 moocow kernel: [14303.454014] scsi3 : SCSI emulation for USB Mass Storage devices
Dec  7 01:14:39 moocow kernel: [14308.452815] scsi 3:0:0:0: Direct-Access     Vivitar  ViviCam6324      1.00 PQ: 0 ANSI: 2
Dec  7 01:14:39 moocow kernel: [14308.457788] sd 3:0:0:0: [sdc] 1984000 512-byte hardware sectors (1016 MB)
Dec  7 01:14:39 moocow kernel: [14308.460773] sd 3:0:0:0: [sdc] Write Protect is off
Dec  7 01:14:39 moocow kernel: [14308.469759] sd 3:0:0:0: [sdc] 1984000 512-byte hardware sectors (1016 MB)
Dec  7 01:14:39 moocow kernel: [14308.472756] sd 3:0:0:0: [sdc] Write Protect is off
Dec  7 01:14:39 moocow kernel: [14308.472769]  sdc: sdc1
Dec  7 01:14:39 moocow kernel: [14308.483799] sd 3:0:0:0: [sdc] Attached SCSI removable disk
Dec  7 01:14:39 moocow kernel: [14308.483862] sd 3:0:0:0: Attached scsi generic sg2 type 0
Dec  7 01:15:10 moocow kernel: [14338.702637] usb 3-1: reset full speed USB device using uhci_hcd and address 6
Dec  7 01:15:20 moocow kernel: [14348.947748] usb 3-1: reset full speed USB device using uhci_hcd and address 6
Dec  7 01:15:20 moocow kernel: [14349.211423] usb 3-1: reset full speed USB device using uhci_hcd and address 6
Dec  7 01:15:30 moocow kernel: [14359.456485] usb 3-1: reset full speed USB device using uhci_hcd and address 6
Dec  7 01:15:31 moocow kernel: [14359.608338] sd 3:0:0:0: scsi: Device offlined - not ready after error recovery
Dec  7 01:15:31 moocow kernel: [14359.608352] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Dec  7 01:15:31 moocow kernel: [14359.608358] end_request: I/O error, dev sdc, sector 1983984
Dec  7 01:15:31 moocow kernel: [14359.608363] printk: 32 messages suppressed.

Does anyone have solutions?

---

