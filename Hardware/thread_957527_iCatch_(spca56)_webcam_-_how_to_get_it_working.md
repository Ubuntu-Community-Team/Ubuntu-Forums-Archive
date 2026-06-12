---
title: "iCatch (spca56) webcam - how to get it working?"
date: 2008-10-24
forum: Hardware
---

### Post by pickarooney on 2008-10-24
I have an iCatch webcam with a spca56 chipset. When I plug it in and type lsusb teh device does not appear. Dmesg give me 
```

[100357.997249] usb 2-4: new full speed USB device using ohci_hcd and address 10
[100358.212394] usb 2-4: configuration #1 chosen from 1 choice

```

**lsmod | grep gspca** gives 
```

gspca                 643920  0
videodev               29440  2 gspca,bttv
usbcore               146028  8 usblp,gspca,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd

```

but I'm not sure what to do next to see if the camera can be used or not.

Any ideas?

---

### Post by cariboo on 2008-10-24
Check to see if your webcam is listed here:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Do a search on the usb id. To do that ina terminal run lsusb, the result should look something like this:

```
lsusb
Bus 002 Device 008: ID 05dc:a575 Lexar Media, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 005: ID **046d:08da** Logitech, Inc. QuickCam Messanger
Bus 001 Device 004: ID 0665:5161  
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

In the above example I bolded the id for my webcam, If your webcam is listed download the driver. It is pretty easy to build the driver.

Make sure you have build-essential installed, then extract the file somewhere in your home directory then in a terminal cd in to the directory just created. to build the driver type:

```
sudo ./gspca_build
```

This will build the driver and insert the module, then install and run cheese and watch yourself on the webcam.

Jim

---

### Post by pickarooney on 2008-10-25
**lsusb** does not list the device at all.
I guess that means it's DOA?

---

### Post by pickarooney on 2008-10-26
Actually, to correct that a bit - when I type lsusb without the camera, then plug it in and type it again, an extra line gets added, but without the device info:
```

Bus 002 Device 006: ID 17a1:0128

```

This happens on two separate PCs with Kubuntu Hardy. I'll cross-test with XP when I get a chance.

---

### Post by pickarooney on 2008-10-30
So, I installed it on Windows XP and it works perfectly. 
I searched for 17a1 on that page and din't find it, so I guess I'm just out of luck as far as linux compatibility goes. :(

According to [this thread](http://ubuntuforums.org/showthread.php?t=832805) there are drivers in development though, so maybe one day it'll work. If not, free webcam for someone.

Stupid eBay! :D

---

### Post by uagner on 2009-02-01
I got the same problem

---

