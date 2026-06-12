---
title: "Where to find Linux driver for laptop WebCam SC-13HDL11939N?"
date: 2015-09-13
forum: Hardware
---

### Post by siggi2 on 2015-09-13
Hi,

my laptop webcam is not working, i.e., if I open cheese, only the little blue LED near the camera goes on, but the picture/video in cheese is black. I used cheese to test the webcam because it would not work with Skype. Where could I find a Linux driver for this webcam, please?

Details:

Notebook: Samsung NP300E5C-S04DE 
Built-in webcam: SC-13HDL11939N
Tripleboot: Windows 8, Ubuntu 14.04 LTS Unity, Centos 7

lsusb -v (only part of the output given):
```

Bus 001 Device 003: ID 2232:1029  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x2232 
  idProduct          0x1029 
  bcdDevice            0.25
  iManufacturer           3 Generic
  iProduct                1 WebCam SC-13HDL11939N
```

From dmesg output:
```
[    1.963083] usb 1-1.4: New USB device found, idVendor=2232, idProduct=1029
[    1.963087] usb 1-1.4: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.963089] usb 1-1.4: Product: WebCam SC-13HDL11939N
[    1.963091] usb 1-1.4: Manufacturer: Generic

[   23.150592] media: Linux media interface: v0.10
[   23.156099] Linux video capture interface: v2.00
[   23.165139] uvcvideo: Found UVC 1.00 device WebCam SC-13HDL11939N (2232:1029)
[   23.176030] input: WebCam SC-13HDL11939N as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input12
[   23.176130] usbcore: registered new interface driver uvcvideo
[   23.176133] USB Video Class driver (1.1.1)
```

With Windows 8's Device Manager, the webcam's manufacturer is given as Realtek/Microsoft.

Please do not assume that I am an expert on lsusb and dmesg, let alone on Linux drivers and webcams!

Thanks,

siggi

---

### Post by dino99 on 2015-09-14
[http://www.linuxquestions.org/questions/slackware-14/how-to-check-and-install-webcam-driver-4175548751-print/](http://www.linuxquestions.org/questions/slackware-14/how-to-check-and-install-webcam-driver-4175548751-print/)

---

### Post by siggi2 on 2015-09-14
Thanks dino99, but the 2 version of the *mplayer.....* command mentioned in the links, did not work, i.e., *mplayer: file not found* etc. And I did not find drivers for webcams.

(mplayer is installed and working)

---

