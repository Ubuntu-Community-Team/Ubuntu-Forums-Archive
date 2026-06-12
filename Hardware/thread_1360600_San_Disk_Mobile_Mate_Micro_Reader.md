---
title: "San Disk Mobile Mate Micro Reader"
date: 2009-12-21
forum: Hardware
---

### Post by tattooed_pariah on 2009-12-21
I'm having trouble mounting a micro sd card reader and couldn't find anyone else using the product name as a search string. Since it's hardware and I didn't see a USB forum, I thought this would be the best place..

This is the product:
[http://www.sandisk.com/products/mobile-memory-products/sandisk-mobilemate-micro-reader?tab=features](http://www.sandisk.com/products/mobile-memory-products/sandisk-mobilemate-micro-reader?tab=features)

I'm running 8.04 Hardy Heron, but the last time I was able to download updates was late July 2009. Currently I do not have the ability to download anything on my laptop, I'm deployed and the IT guys don't take kindly to us plugging our personal systems into their network..

When I plug in the micro reader, it shows up as "USB Drive" of unknown type/size/anything else.

In another thread about usb devices, someone recommended the person run "tail -f /var/log/messages" so here is what I see when I run that:

Dec 21 01:49:28 Insanity Kernal: [398390.16855] usb 3-1: new high speed USB device using ehci_hcd and address 45
Dec 21 01:49:28 Insanity Kernal: [448189.511238] usb 3-1: new high speed USB device using ehci_hcd and address 46
Dec 21 01:49:28 Insanity Kernal: [448189.654786] usb 3-1: configuration #1 chosen from 1 choice
Dec 21 01:49:33 Insanity Kernal: [448189.667291] scsi6 : SCSI emulation for USB Mass Storage Devices
Dec 21 01:49:28 Insanity Kernal: [897088.026464] scsi 6:0:0:0: Direct-Access Generic STORAGE DEVICE 9407 PQ: 0 ANSI: 0
Dec 21 01:49:28 Insanity Kernal: [897088.040701] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Dec 21 01:49:28 Insanity Kernal: [897088.040787] sd 6:0:0:0: Attached scsi generic sg2 type 0

I'm pretty much a noob, so please bear with me, what I understand of that is that the system mounted the usb card as a generic scsi device. However when I try to open the "USB Drive" it tells me:

"Unable to mount location, no media in the drive"

I've tried with two different Micro SD HC cards that worked fine on my XP box before I left for deployment.

Is there something I need to enable/disable? can I manually mount the cards since the card reader seems to auto-mount successfully..

Any suggestions would be appreciated! 

Thanks!

---

### Post by tattooed_pariah on 2009-12-30
*BUMP*

anyone have any ideas? did I not give enough information? or the wrong info? am I in the wrong section of the the forums?

---

