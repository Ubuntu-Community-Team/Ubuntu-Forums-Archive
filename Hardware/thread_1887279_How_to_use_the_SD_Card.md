---
title: "How to use the SD Card?"
date: 2011-11-26
forum: Hardware
---

### Post by Metamence on 2011-11-26
Hello, I'm a beginner photographer and I need to be able to use my SD card reader on my laptop. Likewise, I'm new to Ubuntu (11.10) and I don't get a prompt when I plug in my SD card and I can't find it in any directory. Is it even detecting  my SD card?

---

### Post by Mark_in_Hollywood on 2011-11-26
Not quite enough info to troubleshoot, but try this:

in a terminal OR from the Ubuntu Software Center install Shotwell.

the terminal command is:

sudo apt-get install shotwell

If it isn't already installed, it will install. If apt-get installs it, reboot. 

Plug the device into your card reader or the camera into the 'puter via the USB cable.

Shotwell should open and show you the importable photos.

However, just to be certain, in a terminal type:


lsusb

and post the output of that here in this thread. MAYBE the SD card will be seen as a USB device.

---

### Post by Metamence on 2011-11-26
I have shotwell installed but it doesn't show the importable photos.

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 008 Device 002: ID 1bcf:000a Sunplus Innovation Technology Inc. 

```

---

### Post by Mark_in_Hollywood on 2011-11-26
OK, it does not look like Ubuntu is "seeing" the card. So, next, what laptop maker and model are you using. Also, the camera maker, model as well as the maker and model (and size) of the SD card, please.

Do you have any other way of testing the SD card? My printer has ports for SD, CF and other cards. It's slow, but effective.

And, as a backup idea, can you use a USB cable from the camera to the laptop?

---

### Post by Metamence on 2011-11-26
I'm using a Gateway MD7801U and a Nikon D3100 camera. Also using the default SD card that came with my camera which is a Sandisk Extreme HD Video 4 GB.
Unfortunately my camera did not come with a USB cable, however my SD card works on other computers.

---

### Post by Mark_in_Hollywood on 2011-11-26
I could be wrong, but the Nikon you have does have a USB port, according to the Nikon webpage:

[http://www.nikonusa.com/Nikon-Products/Product/Digital-SLR-Cameras/25472/D3100.html#tab-ProductDetail.ProductTabs.TechSpecs](http://www.nikonusa.com/Nikon-Products/Product/Digital-SLR-Cameras/25472/D3100.html#tab-ProductDetail.ProductTabs.TechSpecs)

please see towards the bottom at: Interface

As for the laptop & SD card, I see nothing on the 'net about Linux/Ubuntu, so if you can attach a USB cable that will do for now? If you want to use the SD card, we are going to use a LiveCD (or live-thumb-drive) to boot and look for the sd card. Let me know.

---

### Post by Metamence on 2011-11-26
> **Mark_in_Hollywood said:**
> I could be wrong, but the Nikon you have does have a USB port, according to the Nikon webpage:

[http://www.nikonusa.com/Nikon-Products/Product/Digital-SLR-Cameras/25472/D3100.html#tab-ProductDetail.ProductTabs.TechSpecs](http://www.nikonusa.com/Nikon-Products/Product/Digital-SLR-Cameras/25472/D3100.html#tab-ProductDetail.ProductTabs.TechSpecs)

please see towards the bottom at: Interface

As for the laptop & SD card, I see nothing on the 'net about Linux/Ubuntu, so if you can attach a USB cable that will do for now? If you want to use the SD card, we are going to use a LiveCD (or live-thumb-drive) to boot and look for the sd card. Let me know.
I appreciate the help, but I guess I'll just use Windows (I dual boot Ubuntu) whenever I need to import photos. Thanks though.

---

