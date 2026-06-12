---
title: "NEW Notebook, Fujitsu Siemens Si 2636, Webcam Problem!"
date: 2008-06-23
forum: Hardware
---

### Post by starfly on 2008-06-23
Hello,

Ive got an new Notebook the Fujitsu siemens Si 2636, real Powerbook ;-)

Everything worked out of the box, exluded the Webcam.
I Dont know the producer ( 1,3MP Webcam)....

Heres my Dmesg output, sorry for my bad English !

[ 2060.786722] usb 4-6: new high speed USB device using ehci_hcd and address 6
[ 2061.198668] usb 4-6: configuration #1 chosen from 1 choice
[ 2061.198858] uvcvideo: Found UVC 1.00 device USB2.0 Camera (5986:0202)
[ 2061.463898] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb4/4-6/4-6:1.0/input/input14
[ 2061.640029] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp. 26).


What 2 do, to get it working, then its again a Perfekt Linux ;-)

Thanks a lot !!!!!!

---

### Post by starfly on 2008-06-23
No one a cloue ?!

Its a Bison Webcam

---

### Post by starfly on 2008-06-23
Ive got IT, 4 ALL Bison Cams !


These are the steps I followed:

    * download linux uvc driver from here, following the instructions reported on the site:

      [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

    * edit Makefile and change:
      Code:

      INSTALL_MOD_DIR	:= ubuntu/media/usbvideo

    * edit uvc_video.c and comment out:
      Code:

      /*if (ret != size) {
      		uvc_printk(KERN_ERR, "Failed to query (%u) UVC control %u "
      			"(unit %u) : %d (exp. %u).\n", query, cs, unit, ret,
      			size);
      		return -EIO;
      }*/

      This will simply bypass the check routine that fails on our laptop...

    * make and sudo make install should install the new driver (it will overwrite standard ubuntu modules so you'll probably have harmless checksum errors when those packages will be removed/upgraded, but that can be easily workedaround)

    * eventually rmmod uvcvideo and reattach the camera and it should work, at least it does for me!


Please, if you can, confirm that's working for you too in order to help having this fixed in the next releases!

Bye and enjoy the cam!

---

### Post by smaba on 2008-08-15
nope... this doesn't work for me. I have a Bison cam integrated in my Zepto Znote 6615WD Laptop. This is what lsusb gives me:

~/trunk$ lsusb
Bus 005 Device 004: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 003: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


But I don't get any pictures neither in cheese, skype, camorama or kdetv.

I'm using kubuntu Hardy on a 64bit machine.

Any ideas why it doesn't work?

greets 

smaba

---

### Post by smaba on 2008-08-16
it strangely works on kopete, but not with pigdin or skype etc.

---

