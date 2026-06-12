---
title: "Webcam Genius iLook 300"
date: 2009-06-05
forum: Hardware
---

### Post by PanchoPonceN on 2009-06-05
Hi everyone!

I can't use this webcam I just bought (Genius iLook 300) on Linux Mint 7, an Ubuntu 9.04 based distro. Programs like Cheese or Skype don't detect it because I have no /dev/video0 (or any /dev/video* at all). When I connect it, its little green light turns on and dmesg shows it as

```
[  711.352011] usb 3-1: new full speed USB device using uhci_hcd and address 3
[  711.556351] usb 3-1: configuration #1 chosen from 1 choice
```

It also does appear with lsusb command as

```
Bus 003 Device 003: ID 093a:2628 Pixart Imaging, Inc.
```

I've searched a lot, but no tutorials on Google have helped. If you need more data, just ask. Any help would be greatly appreciated! :)

---

### Post by PanchoPonceN on 2009-06-06
Really? Nobody can help me? :(

---

### Post by kapitanbar on 2009-06-15
I have the same webcam and I can't make it work also.

---

### Post by diego.oro on 2009-06-24
I have the same problem, i think there is not a driver for this camera yet. :(

---

### Post by gabak on 2009-12-31
hey did you find the driver for that webcam??
[http://mxhaard.free.fr/embedded.html](http://mxhaard.free.fr/embedded.html) here i found something but i dont know how to download those files and use that driver some forums talks about getting them via synaptic but synaptic does nt find them

---

### Post by gabak on 2009-12-31
[http://mxhaard.free.fr/spca5le.html](http://mxhaard.free.fr/spca5le.html)

Download and Patch
spca5xx-LE is provide as patch to the main kernel for convenience
to set up the patch you need the compressed patch:
usb-2.4.31LE06.patch.gz is the kernel patch to apply at the 2.4.31 kernel
or linux-2.4.31LE08.patch.tar.gz full kernel patch with support of the Usb Wifi ZD1211 and RT2570

	
	patch -p1 < usb-2.4.31LE06.patch in the usb subdirectory of the kernel
	or
	patch -p1 < linux-2.4.31LE08.patch for the full kernel
your kernel have now support for the spca5xx-LE webcams as the other (ov511 pwc ....)
and maybe some Usb Wifi adaptator like the Linksys WUSB54GV4 or the D-LINK DWL-122 B1 or the Sitecom WL-113 :)
you need to configure the kernel with 
	make menuconfig
	and update the fields if needed:
		CONFIG_MODULES=y
		CONFIG_VIDEO_DEV=m
		CONFIG_USB=y
		CONFIG_USB_DEVICEFS=y
		CONFIG_USB_SPCA5XX=m
	save exit 
then compile
	make 
	make modules

---

### Post by Amr_not_Amr on 2010-04-24
Finally I got my Genius iLook 300 to work on karmic .. other webcams should work too .. 
You can follow the steps explain here [http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/) and your webcam will work...

---

### Post by sgromano on 2010-04-24
> **Amr_not_Amr said:**
> Finally I got my Genius iLook 300 to work on karmic .. other webcams should work too .. 
You can follow the steps explain here [http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/) and your webcam will work...

These instructions are really good. Thank you. 

They allowed me to install latest gspca module on Ubuntu 9.10 (2.6.31-20-server). 

Unfortunately, although lsusb shows that my cam is recognized
Bus 002 Device 002: ID 093a:2628 Pixart Imaging, Inc

/dev/video0 is present.

and lsmod shows:
gspca_pac7302 12352 0
gspca_main 29088 1 gspca_pac7302
videodev 45120 1 gspca_main

I can't use my cam with any application (tried only with Camorama and Skype actually). Message is just “unable to capture image”

---

### Post by Stemp on 2010-05-15
> **sgromano said:**
> I can't use my cam with any application (tried only with Camorama and Skype actually). Message is just “unable to capture image”

I hope it's not too late for an answer.
camorama and skype doesn't use the V4L2 system.

In order to use them you need to add the compatibility or conversion layer :

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
```

or 

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

---

