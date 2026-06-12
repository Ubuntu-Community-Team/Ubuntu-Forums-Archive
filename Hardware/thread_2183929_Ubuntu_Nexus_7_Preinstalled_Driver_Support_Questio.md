---
title: "Ubuntu Nexus 7 Preinstalled Driver Support Question"
date: 2013-10-26
forum: Hardware
---

### Post by jobmo on 2013-10-26
Hi all,
I had an interesting idea for a project and I hit a small snag in terms of driver support. I recently bought a 3d printer and I though it would be cool to use my nexus 7 as a touch interface for it, using a USB OTG cable. I figured it should be easy as the software is python and the print controller is just a standard USB Serial device. 

I went and grabbed a copy of the Raring Preinstalled image for a nexus 7 (not Ubuntu touch, just a full desktop version of Ubuntu for a nexus 7) and put it on my nexus. I tested my USB OTG cable with a flash drive, and it worked great. I then grabbed the software and got that running, the last step was just to connect it over USB... then failure. My Nexus 7 does not recognize the serial USB device.

If I do an lsusb with the flash drive in I get the following:
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0781:5530 SanDisk Corp. Cruzer

```

with the printer plugged in all I see is:
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

w/o the USB OTG cable i see:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I know the VID is 16c0 and the PID is 0483, and if I run 
```
 dmesg | grep 16c0
```
I get:

```
[10009.070968] usb 2-1: New USB device found, idVendor=16c0, idProduct=0483
```

I am beginning to wonder if the serial usb support was yanked from the Nexus 7 preinstall image (because who the hell would need those right). Any one have any ideas or possibly know how I could install serial usb support?

---

### Post by jobmo on 2013-10-27
Figures that shortly after asking the question I would resolve it myself... figures. The answer was to run:
```

sudo modprobe usbserial vendor=0x16c0 product=0x0483

```

---

