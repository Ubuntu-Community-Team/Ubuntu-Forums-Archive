---
title: "trying to read motorola z6c"
date: 2009-01-16
forum: Hardware
---

### Post by digitalramble on 2009-01-16
Hi, all.  I'm trying to get my setup (8.10) to recognize my motorola z6c.  I am not trying to sync or anything fancy; I really would be thrilled if I could treat it like a mass storage device.  (I primarily want to pull off the text messages and the pictures from the phone.)

I have the proper usb/mini usb data cable for it.  When I plug it into my laptop, it starts to charge up.

dmesg gives me:
[ 5091.616240] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 5091.856245] usb 1-2: new full speed USB device using uhci_hcd and address 2
[ 5092.019445] usb 1-2: configuration #1 chosen from 1 choice


(which doesn't sound good, actually).

I'm looking at kmobiletools but am at a loss how to configure it (I haven't even the faintest idea where it would be -- it certainly doesnt' seem to be mounted on /dev/mobile ).

Any information, pointers to information, or suggestions would be gratefully entertained...

---

