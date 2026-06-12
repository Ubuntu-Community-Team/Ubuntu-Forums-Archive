---
title: "HP Photosmart R707 not mounting anymore in 7.10 gutsy gibbon"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by gaupe on 2007-10-19
I changed to Ubuntu 7.10 gutsy gibbon  and suddenly my digital camera a hp Photosmart R707 doesnt mount anymore.

It did work flawlessly in feisty fawn so what i did now is boot from ubuntu 7.4 and do a sylog

Down i show two logfiles from /var/syslog for both ubuntu versions. These are untouched cd boots. 
what you see is that in the bottom one (gutsy gibbon) the usb bus is resetted again apperently the communication does not go right after initially the camera is recognised 

Does Anybody recognise if this is a know bug?
is there anyone who has a solution to this?


syslog for a good mount in feisty fawn
```

Oct 19 17:45:06 ubuntu kernel: [  427.468000] usb 1-1: new full speed USB device using uhci_hcd and address 5
Oct 19 17:45:06 ubuntu kernel: [  427.644000] usb 1-1: configuration #1 chosen from 1 choice
Oct 19 17:45:06 ubuntu kernel: [  427.648000] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 19 17:45:11 ubuntu kernel: [  432.656000] scsi 4:0:0:0: Direct-Access     HP       PhotoSmart R707  A001 PQ: 0 ANSI: 0
Oct 19 17:45:11 ubuntu kernel: [  432.660000] SCSI device sdc: 499713 512-byte hdwr sectors (256 MB)
Oct 19 17:45:11 ubuntu kernel: [  432.664000] sdc: Write Protect is off
Oct 19 17:45:11 ubuntu kernel: [  432.672000] SCSI device sdc: 499713 512-byte hdwr sectors (256 MB)
Oct 19 17:45:11 ubuntu kernel: [  432.676000] sdc: Write Protect is off
Oct 19 17:45:11 ubuntu kernel: [  432.676000]  sdc: sdc1
Oct 19 17:45:11 ubuntu kernel: [  432.684000] sd 4:0:0:0: Attached scsi removable disk sdc
Oct 19 17:45:11 ubuntu kernel: [  432.684000] sd 4:0:0:0: Attached scsi generic sg3 type 0

```


syslog for a no mount and hang of the camera in gutsy gibbon

```

Oct 19 17:58:48 ubuntu kernel: [  272.524000] usb 1-1: new full speed USB device using uhci_hcd and address 4
Oct 19 17:58:48 ubuntu kernel: [  272.700000] usb 1-1: configuration #1 chosen from 1 choice
Oct 19 17:58:48 ubuntu kernel: [  272.752000] scsi3 : SCSI emulation for USB Mass Storage devices
Oct 19 17:58:53 ubuntu kernel: [  277.756000] scsi scan: INQUIRY result too short (5), using 36
Oct 19 17:58:53 ubuntu kernel: [  277.756000] scsi 3:0:0:0: Direct-Access     HP       PhotoSmart R707  A001 PQ: 0 ANSI: 0
Oct 19 17:58:53 ubuntu kernel: [  277.760000] sd 3:0:0:0: [sdc] 499713 512-byte hardware sectors (256 MB)
Oct 19 17:58:53 ubuntu kernel: [  277.764000] sd 3:0:0:0: [sdc] Write Protect is off
Oct 19 17:58:53 ubuntu kernel: [  277.772000] sd 3:0:0:0: [sdc] 499713 512-byte hardware sectors (256 MB)
Oct 19 17:58:53 ubuntu kernel: [  277.776000] sd 3:0:0:0: [sdc] Write Protect is off
Oct 19 17:58:53 ubuntu kernel: [  277.776000]  sdc: sdc1
Oct 19 17:58:53 ubuntu kernel: [  277.784000] sd 3:0:0:0: [sdc] Attached SCSI removable disk
Oct 19 17:58:53 ubuntu kernel: [  277.784000] sd 3:0:0:0: Attached scsi generic sg3 type 0
Oct 19 17:59:23 ubuntu kernel: [  308.128000] usb 1-1: reset full speed USB device using uhci_hcd and address 4
Oct 19 17:59:34 ubuntu kernel: [  318.388000] usb 1-1: reset full speed USB device using uhci_hcd and address 4
Oct 19 17:59:39 ubuntu kernel: [  323.648000] usb 1-1: reset full speed USB device using uhci_hcd and address 4
Oct 19 17:59:49 ubuntu kernel: [  333.908000] usb 1-1: reset full speed USB device using uhci_hcd and address 4
Oct 19 17:59:49 ubuntu kernel: [  334.056000] sd 3:0:0:0: scsi: Device offlined - not ready after error recovery
Oct 19 17:59:49 ubuntu kernel: [  334.056000] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 19 17:59:49 ubuntu kernel: [  334.056000] end_request: I/O error, dev sdc, sector 499712

```

---

### Post by duruttye on 2007-10-21
Hey!

Same problem here, the syslog is similar.

Anyone, with some ideas...

thanx

---

