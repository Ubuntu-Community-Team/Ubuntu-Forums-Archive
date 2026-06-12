---
title: "Voicerecorder"
date: 2009-06-04
forum: Hardware
---

### Post by Q-collective on 2009-06-04
Hey all! :)

I do some amateur journalistic work and a voicerecorder is a musthave really. Currently I'm using an Olympus voicerecorder, which seems to have zero support in Linux. Ubuntu simply doesn't see it. After some googling around, I noticed Olympus is notorious for its lack of Linux support...

So, are there any recommendations on a good voicerecorder for Linux? Mind that I'm actually looking for something that is very portable, [like the Olympus stuff]("http://www.olympusamerica.com/cpg_section/cpg_vr_digitalrecorders.asp"). Walking with my laptop with a mic plugged in is not an option.

Thanks in advance!

---

### Post by Oswaldroy on 2009-06-04
Now you are able to use the mp4 pen which is fully compatible in ubuntu. It hosts a camrea too for you with 1Gb storage.
[http://www.everythingusb.com/dvr-camcorder-pen-camera-recorder-14920.html](http://www.everythingusb.com/dvr-camcorder-pen-camera-recorder-14920.html)

---

### Post by Q-collective on 2009-06-04
> **Oswaldroy said:**
> Now you are able to use the mp4 pen which is fully compatible in ubuntu. It hosts a camrea too for you with 1Gb storage.
[http://www.everythingusb.com/dvr-camcorder-pen-camera-recorder-14920.html](http://www.everythingusb.com/dvr-camcorder-pen-camera-recorder-14920.html)
This seems a bit overkill for my needs. I need good quality sound, video is not needed. If a mp3 player with a mic can provide high quality sound recordings, I'll look into that.

---

### Post by Q-collective on 2009-06-04
I just bought myself a [Velleman MVR2](http://www.velleman.be/nl/en/product/view/?id=377348) and it works plug-n-play!

This is solved :D

---

### Post by Q-collective on 2009-07-04
Ok, not so anymore. I reinstalled Ubuntu 9.04 and now it suddenly doesn't automount it anymore for some reason. This is what dmesg spits out:

```
[  784.184051] hub 2-0:1.0: over-current change on port 1
[  784.288060] hub 3-0:1.0: over-current change on port 1
[  784.392061] hub 1-0:1.0: over-current change on port 1
[  784.680076] hub 1-0:1.0: over-current change on port 3
[  785.080048] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  785.204054] usb 2-1: device descriptor read/64, error -71
[  785.432041] usb 2-1: device descriptor read/64, error -71
[  785.648057] usb 2-1: new low speed USB device using uhci_hcd and address 3
[  785.772054] usb 2-1: device descriptor read/64, error -71
[  786.009546] usb 2-1: device descriptor read/64, error -71
[  786.224060] usb 2-1: new low speed USB device using uhci_hcd and address 4
[  786.640060] usb 2-1: device not accepting address 4, error -71
[  786.752071] usb 2-1: new low speed USB device using uhci_hcd and address 5
[  787.168056] usb 2-1: device not accepting address 5, error -71
[  787.168083] hub 2-0:1.0: unable to enumerate USB device on port 1

```
What is happening?

---

