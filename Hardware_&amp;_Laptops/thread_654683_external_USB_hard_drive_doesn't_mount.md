---
title: "external USB hard drive doesn't mount"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by dormant on 2007-12-31
I am having problems with an external bus-powered USB hard drive.

The drive is new, but was working perfectly under Ubuntu 7.10 until the following series of events.

[LIST]
[*]Someone else tried to read it on a Mac, unsuccesfully.
[*]Someone else succesfully read it on Windows (XP I think).
[*]I mounted the disk in Ubuntu 7.10
[*]I emptied the trash on this disk
[*]I deleted one file, which had a weird name I can't remember but I thought it was a windows or mac file - I think it started with a $..
[*]I tried writing to the disk, but got an error message.
[*]The disk disappeared from my mount.
[/LIST]

I was present when these happened, but don't know what the Mac problem was (some Mac people don't make much sense).

Ever since, it won't mount. Both in Ubuntu (on three different machines) and in Windows, both XP and Vista.

Sometimes it appears in lsusb, but then disappears..

dmesg gives the following
> ...
[ 1271.532000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[ 1271.644000] usb 5-6: device descriptor read/64, error -71
[ 1271.860000] usb 5-6: device descriptor read/64, error -71
[ 1272.076000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[ 1272.188000] usb 5-6: device descriptor read/64, error -71
[ 1272.404000] usb 5-6: device descriptor read/64, error -71
[ 1272.620000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[ 1273.028000] usb 5-6: device not accepting address 4, error -71
[ 1273.140000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[ 1273.548000] usb 5-6: device not accepting address 4, error -71
[ 1273.548000] usb 5-6: USB disconnect, address 4
[ 1273.660000] usb 5-6: new high speed USB device using ehci_hcd and address 5
[ 1273.772000] usb 5-6: device descriptor read/64, error -71
[ 1273.988000] usb 5-6: device descriptor read/64, error -71
[ 1274.204000] usb 5-6: new high speed USB device using ehci_hcd and address 6
[ 1274.316000] usb 5-6: device descriptor read/64, error -71
[ 1274.532000] usb 5-6: device descriptor read/64, error -71
[ 1274.748000] usb 5-6: new high speed USB device using ehci_hcd and address 7
[ 1275.156000] usb 5-6: device not accepting address 7, error -71
[ 1275.276000] usb 5-6: new high speed USB device using ehci_hcd and address 8
[ 1275.684000] usb 5-6: device not accepting address 8, error -71


Any suggestions how to proceed. Unfortunately, I have some important data on the disk, so would like to rescue it.

---

### Post by dormant on 2007-12-31
I fixed it. But I'm not sure how.

I booted into Windows to look at the CD Freecom supplied with the USB HD, in the vague hope that there might be some rescue software. There wasn't, but I decided to install the software in the vaguer hope that it might have a super-duper driver.

And then I plugged the USB drive in and it mounted.

And it also mounts in Ububtu. The two files I deleted from the trash have returned. As has the folder $RECYCLE.BIN, which was the mystery file I also deleted.

Phew!

---

