---
title: "One more iPod thread -- 2nd Gen Shuffle Not Recognized"
date: 2009-08-15
forum: Hardware
---

### Post by dogeatery on 2009-08-15
Because there aren't enough iPod threads around here ...  

I've had pretty good luck with getting my iPod to work in Ubuntu, but today I plugged it in and the computer doesn't recognize it at all.  I did ```
$ lsusb
``` and it didn't show anything plugged in.  The little orange light blinks once, very quickly, and then it just sits there.  I've tried restarting the computer, unplugging and re-plugging, etc.  All to no avail.  I have no idea if it's even receiving a charge.  Usually it flashes as long as it's plugged in. Other USB devices seem to work fine, including a portable HDD and USB Skype phone.  When I type ```
$ lsusb
``` the HDD is recognized, but still not the iPod.

Searching threads here, I haven't found anyone with quite the same problem and so posted the new thread.  I'm running the latest version of Linux Mint with Gnome.

Update:```
 $ dmesg

[ 1087.425266] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1097.976069] usb 3-1: new full speed USB device using uhci_hcd and address 22
[ 1098.100083] usb 3-1: device descriptor read/64, error -71
[ 1098.328076] usb 3-1: device descriptor read/64, error -71
[ 1098.544066] usb 3-1: new full speed USB device using uhci_hcd and address 23
[ 1098.664056] usb 3-1: device descriptor read/64, error -71
[ 1098.888084] usb 3-1: device descriptor read/64, error -71
[ 1099.104063] usb 3-1: new full speed USB device using uhci_hcd and address 24
[ 1099.512080] usb 3-1: device not accepting address 24, error -71
[ 1099.624068] usb 3-1: new full speed USB device using uhci_hcd and address 25
[ 1100.032060] usb 3-1: device not accepting address 25, error -71
[ 1100.032086] hub 3-0:1.0: unable to enumerate USB device on port 1
[ 1143.060085] usb 3-1: new full speed USB device using uhci_hcd and address 26
[ 1143.184069] usb 3-1: device descriptor read/64, error -71
[ 1143.412063] usb 3-1: device descriptor read/64, error -71
[ 1143.628076] usb 3-1: new full speed USB device using uhci_hcd and address 27
[ 1143.748066] usb 3-1: device descriptor read/64, error -71
[ 1143.972077] usb 3-1: device descriptor read/64, error -71
[ 1144.188074] usb 3-1: new full speed USB device using uhci_hcd and address 28
[ 1144.596063] usb 3-1: device not accepting address 28, error -71
[ 1144.708066] usb 3-1: new full speed USB device using uhci_hcd and address 29
[ 1145.116072] usb 3-1: device not accepting address 29, error -71
[ 1145.116097] hub 3-0:1.0: unable to enumerate USB device on port 1

```The above USB errors come at the end of the dmesg output.  I hope somebody knows what to make of it?

UPDATE:

I guess I'm an idiot ... I continued impatiently unplugging and re-inserting the USB attachment and the iPod decided to just start working again.

---

