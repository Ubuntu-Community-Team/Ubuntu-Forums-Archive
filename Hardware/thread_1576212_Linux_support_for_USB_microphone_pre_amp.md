---
title: "Linux support for USB microphone pre amp"
date: 2010-09-16
forum: Hardware
---

### Post by Nerevar144 on 2010-09-16
Does anyone know if there's any sort of support on Ubuntu for the ART MP Tube Project Series pre amp w/USB.  Here's the company's link to the product in question:

[http://artproaudio.com/products.asp?id=124&cat=9&type=86](http://artproaudio.com/products.asp?id=124&cat=9&type=86)

I'm running Xubuntu 10.04, and it's not sensed in the audio hardware tab, only the internal sound card is.  Can't select it in Audacity  or Ardour.  On Windows there are no drivers to install, it just pops us as USB Audio CODEC when you plug it in... which sounds pretty generic, so I was hoping there was some sort of generic driver for it.  I doubt there's a driver written specifically for it.  Any input is appreciated.

---

### Post by IcarusR on 2010-09-17
Does ubuntu see it ? Is there any mention of it in the log files ?
Is it listed in the output of this terminal command ?

```
lsusb
```

---

### Post by Nerevar144 on 2010-10-26
Here's the output from lsusb:

```
:~$ lsusb
Bus 002 Device 003: ID 1532:0016 Razer USA, Ltd 
Bus 002 Device 002: ID 03f0:8104 Hewlett-Packard Printing Support
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 001 Device 002: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

it looks like it's not there.  What are my chances of getting this working now?

---

### Post by Nerevar144 on 2010-11-04
Bump!

Also, I just discovered that there are Windows ASIO drivers located at [www.asio4all.com](www.asio4all.com) and [www.usb-audio.com](www.usb-audio.com).  Does this give anymore hope?

---

### Post by Nerevar144 on 2010-11-18
Looks like no support ](*,)

---

### Post by Nerevar144 on 2010-11-18
I've been continuing my search and according to linuxstudiopro.com another ART preamp (the ART USB Dual Pre Microphone Preamp and Interface) is supported via the module: snd-usb-audio.  How can I check if mine is?  I don't know much about this snd-usb-audio module.........

Any help is GREATLY appreciated.  My goal here is to get a netbook and run ubuntu on it for use as a mobile recording platform...

---

