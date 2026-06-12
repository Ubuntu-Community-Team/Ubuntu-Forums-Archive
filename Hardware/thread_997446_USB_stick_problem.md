---
title: "USB stick problem"
date: 2008-11-29
forum: Hardware
---

### Post by fessio on 2008-11-29
Hi, everyone.
Today I bought a Transcend 4gb flash stick for making an openSuse-KDE4-Live liveUSB from it to test the beta. I followed this tutorial ( [link here]("http://lizards.opensuse.org/2008/05/31/making-opensuse-110-liveusb-the-easiest-and-fastest-way/")). But when I rebooted, the computer didn't boot from it(the boot priorities were set right). So I decided to try to toggle its boot flag in "fdisk". And that's where the problem appeared, after rebooting it did not boot to flash AND the system couldn't see my stick anymore!

the output of "sudo fdisk /dev/sdb":
```
Unable to open /dev/sdb
```

the output of dmesg right after plugging the stick in:

```
[  789.116156] usb 5-2: new high speed USB device using ehci_hcd and address 5
[  789.307855] usb 5-2: configuration #1 chosen from 1 choice
[  789.313970] scsi5 : SCSI emulation for USB Mass Storage devices
[  789.317036] usb-storage: device found at 5
[  789.317044] usb-storage: waiting for device to settle before scanning
[  794.317061] usb-storage: device scan complete
[  794.318073] scsi 5:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
[  794.331648] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  794.332065] sd 5:0:0:0: Attached scsi generic sg2 type 0
```

GParted doesn't see it either.

Besides windows now sees it as a card reader, meaning that when I try to access it, it tells to insert a drive in it. Does it mean that my new usb stick is dead?

I would be glad if you helped me :( Thanks

---

