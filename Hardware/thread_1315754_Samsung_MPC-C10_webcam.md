---
title: "Samsung MPC-C10 webcam"
date: 2009-11-05
forum: Hardware
---

### Post by goldencako on 2009-11-05
Hey, I have a really old webcam, the Samsung MPC-C10. I tried to plug it in just to see if i worked and I got this:
```
cako@lynx2:~$ dmesg | tail -11[INDENT][ 1423.193212] usb 3-1: new full speed USB device using uhci_hcd and address 14
[ 1423.316057] usb 3-1: device descriptor read/64, error -71
[ 1423.540067] usb 3-1: device descriptor read/64, error -71
[ 1423.760168] usb 3-1: new full speed USB device using uhci_hcd and address 15
[ 1423.880048] usb 3-1: device descriptor read/64, error -71
[ 1424.104058] usb 3-1: device descriptor read/64, error -71
[ 1424.320062] usb 3-1: new full speed USB device using uhci_hcd and address 16
[ 1424.732048] usb 3-1: device not accepting address 16, error -71
[ 1424.844058] usb 3-1: new full speed USB device using uhci_hcd and address 17
[ 1425.252051] usb 3-1: device not accepting address 17, error -71
[ 1425.252083] hub 3-0:1.0: unable to enumerate USB device on port 1
[/INDENT]

```

Any clues on how to get it to work? This is by no means urgent, I was just wondering I someone has gotten a similar camera to work.

Thanks

---

### Post by no2498 on 2009-11-05
do you have any programs like cheese or wxcam to help you set the dev video after you get 1 of them
open the terminal type ( lusb ) hit enter post the list back here
also in the terminal type ( gstreamer-properties )hit enter
click video try diff settings if it comes on your on your way

---

### Post by goldencako on 2009-11-05
I tried cheese and it didn't recognize it. I also tried testing different gstreamer setting and none worked. They said there was no video0. So, my camera is not even being recognized as a camera.

I don't have lusb installed and it's not on the repos. Sure that's the right command?

---

### Post by no2498 on 2009-11-28
it was not it is ( lsusb )

---

