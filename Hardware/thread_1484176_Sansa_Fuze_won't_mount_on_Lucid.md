---
title: "Sansa Fuze won't mount on Lucid"
date: 2010-05-15
forum: Hardware
---

### Post by ennoil on 2010-05-15
I have a Sansa Fuze 4GB mp3 player. This device mounted fine on Karmic.
Now when I plug the device in I see the following in /var/log/messages:

May 15 11:11:54 jkennedy-D630 kernel: [ 1045.140127] usb 2-1: USB disconnect, address 6
May 15 11:13:48 jkennedy-D630 kernel: [ 1158.960067] usb 5-1: new full speed USB device using uhci_hcd and address 4
May 15 11:13:51 jkennedy-D630 kernel: [ 1161.570086] usb 2-1: new high speed USB device using ehci_hcd and address 8
May 15 11:13:51 jkennedy-D630 kernel: [ 1161.724771] usb 2-1: configuration #1 chosen from 1 choice
May 15 11:13:51 jkennedy-D630 kernel: [ 1161.730743] scsi7 : SCSI emulation for USB Mass Storage devices
May 15 11:14:17 jkennedy-D630 kernel: [ 1188.130165] usb 2-1: reset high speed USB device using ehci_hcd and address 8
May 15 11:14:18 jkennedy-D630 kernel: [ 1188.970204] usb 2-1: reset high speed USB device using ehci_hcd and address 8
May 15 11:14:25 jkennedy-D630 kernel: [ 1195.510204] usb 2-1: reset high speed USB device using ehci_hcd and address 8
May 15 11:14:25 jkennedy-D630 kernel: [ 1196.060095] usb 2-1: reset high speed USB device using ehci_hcd and address 8
May 15 11:14:26 jkennedy-D630 kernel: [ 1196.990065] usb 2-1: reset high speed USB device using ehci_hcd and address 8
May 15 11:14:27 jkennedy-D630 kernel: [ 1197.449086] scsi 7:0:0:0: Device offlined - not ready after error recovery

When the resets happen, the Fuze shows that it is "Writing". I can not see the device in lsusb, udisks, or using any graphical means. What has changed to cause this and is there a work around?

I get the same when I try on my Aspire One running UNR 10.04.

Thanks,
John

PS - I can mount the device on openSUSE 11.2 so it may not be an Ubuntu specific thing. Would have to test and see if it fails to mount on 11.3 to confirm but I do not have the time to install just to test...

---

### Post by dino99 on 2010-05-15
sudo update-pciids && update-usbids

[http://forums.sandisk.com/sansa/board/message?board.id=clipplus&thread.id=5040](http://forums.sandisk.com/sansa/board/message?board.id=clipplus&thread.id=5040)

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/532237](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/532237)

---

### Post by ennoil on 2010-05-17
Tried what you said and both the links with no luck. I am stumped. Guess I will have to keep my other laptop running OpenSUSE.

---

