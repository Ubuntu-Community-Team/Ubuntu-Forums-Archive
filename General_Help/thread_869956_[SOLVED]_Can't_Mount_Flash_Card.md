---
title: "[SOLVED] Can't Mount Flash Card"
date: 2008-07-25
forum: General Help
---

### Post by gus_zernial on 2008-07-25
I have Kubuntu Hardy 8.04, and I'm trying to mount an 8GB SD Card
in a USB 6-in-1 reader. The storage doesn't mount automatically.
When I plug in the USB reader it seems to recognize the device(s),
but when I try to mount it I get:

$ sudo mount -t vfat /dev/sdc /mnt/usb
mount: /dev/sdc is not a valid block device

And when I try to fdisk it I get:

$ sudo fdisk /dev/sdc
Unable to open /dev/sdc

/dev/sdc1 doesn't work either, and when I try to mount /dev/sdd, e, and f I get "No medium found", so I'm pretty sure /dev/sdc is the SD card. Below is a tail of /var/log/messages when I plug in the reader. I'd appreciate suggestions to diagnose and resolve ...

Jul 25 09:15:04 jboat17 kernel: [ 2759.299401] usb 8-5: configuration #1 chosen from 1 choice
Jul 25 09:15:04 jboat17 kernel: [ 2759.381136] usbcore: registered new interface driver libusual
Jul 25 09:15:04 jboat17 kernel: [ 2759.408541] Initializing USB Mass Storage driver...
Jul 25 09:15:04 jboat17 kernel: [ 2759.408745] scsi6 : SCSI emulation for USB Mass Storage devices
Jul 25 09:15:04 jboat17 kernel: [ 2759.408926] usbcore: registered new interface driver usb-storage
Jul 25 09:15:04 jboat17 kernel: [ 2759.408929] USB Mass Storage support registered.
Jul 25 09:15:09 jboat17 kernel: [ 2764.405266] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Jul 25 09:15:09 jboat17 kernel: [ 2764.405769] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Jul 25 09:15:09 jboat17 kernel: [ 2764.406269] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Jul 25 09:15:09 jboat17 kernel: [ 2764.406769] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Jul 25 09:15:39 jboat17 kernel: [ 2794.514359] usb 8-5: reset high speed USB device using ehci_hcd and address 2
Jul 25 09:15:49 jboat17 kernel: [ 2804.756307] usb 8-5: reset high speed USB device using ehci_hcd and address 2
Jul 25 09:16:05 jboat17 kernel: [ 2821.001075] usb 8-5: reset high speed USB device using ehci_hcd and address 2
Jul 25 09:16:06 jboat17 kernel: [ 2821.251601] usb 8-5: reset high speed USB device using ehci_hcd and address 2
Jul 25 09:16:16 jboat17 kernel: [ 2831.493542] usb 8-5: reset high speed USB device using ehci_hcd and address 2
Jul 25 09:16:16 jboat17 kernel: [ 2831.627311] sd 6:0:0:0: Device offlined - not ready after error recovery
Jul 25 09:16:16 jboat17 kernel: [ 2831.627345] sd 6:0:0:0: [sdc] READ CAPACITY failed
Jul 25 09:16:16 jboat17 kernel: [ 2831.627347] sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jul 25 09:16:16 jboat17 kernel: [ 2831.627350] sd 6:0:0:0: [sdc] Sense not available.
Jul 25 09:16:16 jboat17 kernel: [ 2831.627356] sd 6:0:0:0: [sdc] Write Protect is off
Jul 25 09:16:16 jboat17 kernel: [ 2831.627405] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Jul 25 09:16:16 jboat17 kernel: [ 2831.627438] sd 6:0:0:0: Attached scsi generic sg3 type 0
Jul 25 09:16:16 jboat17 kernel: [ 2831.630979] sd 6:0:0:1: [sdd] Attached SCSI removable disk
Jul 25 09:16:16 jboat17 kernel: [ 2831.631011] sd 6:0:0:1: Attached scsi generic sg4 type 0
Jul 25 09:16:16 jboat17 kernel: [ 2831.638260] sd 6:0:0:2: [sde] Attached SCSI removable disk
Jul 25 09:16:16 jboat17 kernel: [ 2831.638295] sd 6:0:0:2: Attached scsi generic sg5 type 0
Jul 25 09:16:16 jboat17 kernel: [ 2831.640486] sd 6:0:0:3: [sdf] Attached SCSI removable disk
Jul 25 09:16:16 jboat17 kernel: [ 2831.640519] sd 6:0:0:3: Attached scsi generic sg6 type 0

---

### Post by gimlithedwarf on 2008-07-25
can I see the output of ```
ls /dev/ | grep -i sd
``` with the card in and with the card out

---

### Post by moore.bryan on 2008-07-25
and as what does gparted see the partition on the card?

---

### Post by silkstone on 2008-07-25
Does your card reader support SDHC cards? Many older ones do not. If the reader works with lower capacity SD cards (1GB or less), that is likely to be the problem.

You can get a 35-in-1 Hama card reader that does support SDHC from Amazon for less than £5 ($10).

---

### Post by gus_zernial on 2008-07-26
Correct answer is .... my reader didn't support SDHC cards.
Gor a new one, all is well. Thanks silkstone!

---

