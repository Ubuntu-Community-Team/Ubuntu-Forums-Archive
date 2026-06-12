---
title: "Logitech Quickcam Communicate (046d:08f5) not being recognized"
date: 2008-06-28
forum: Hardware
---

### Post by krabator on 2008-06-28
Hi everyone,

I've been spending my whole morning trying to get this darn logitech communicate webcam to work..
I've installed the supposedly correct driver (gspcav1-20061216), and also tried another one (gspcav1-20071224), I followed the instructions, everything is everytime running smooth, no problem whatsoever, but in the end, the webcam isn't detected. Ive looked into /dev, and theres no video0 at all (which for example camorama complains about not being able to connect to). The only change between when the webcam is plugged in and when its not is a "2-2" file that appears when plugged and disappears when not. I've been looking all over for a solution, but to no avail..
could anybody please help me?

I'd be forever thankful..

Jonathan

PS If youre wondering, yes ive checked if my webcam model is supported, and ive made sure my headers, restricted-modules and kernel versions are the same.

---

### Post by krabator on 2008-07-17
My problem is "solved": I found out that qc-usb-messenger-1.8 is the proper driver i was looking for, so now my camera is recognized, Camorama gives me an image (although not the best quality), xawTV gives me a much better image, but skype gives me a less than poor image.. so i hope the linux-skype-team works out a bit their video feature for next release..
But anyways, my main problem is fixed!

---

### Post by Chris_82 on 2010-09-26
Hi there,

I am trying to get that Communicate (046d:08f5) working on Ubuntu 10.04 but I get no image..this is what dmesg is saying:
gspca: probe ok
STV06xx: Probing for a stv06xx device
gspca: probing 046d:08f5

How did you use qc-usb to get yours working?

ps; yes I realize that this thread is old..

cheers.

---

### Post by Paradoxfox93 on 2010-11-05
I'm having the same problem with the same device.  It seems this stv06xx isn't supposed to be doing stuff and is interfering with the gspca

[https://patchwork.kernel.org/patch/84145/](https://patchwork.kernel.org/patch/84145/)

---

