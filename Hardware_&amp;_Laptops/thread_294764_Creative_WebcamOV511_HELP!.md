---
title: "Creative Webcam/OV511 HELP!"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by tetherblood on 2006-11-07
Hi,
Ive just been trying to set up my webcam (Creative Mini. Model **PD0040**) on Ubuntu 6.06
After digging around google for driver info i found this site:

[http://alpha.dyndns.org/ov511/install.html](http://alpha.dyndns.org/ov511/install.html) 

If you browse to the supported camera's it claims my model is supported. To start with i ran the command:
> modprobe ov511
This returned no errors so i skipped to the "Loading the driver" section as advised in the tutorial. 
I check my USB controller which returns:
> 0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)

Then as i try these steps from the tutorial i get no response which the writer claims may mean USB is built into the kernal: (i tried them all after getting no respone from the "UHCI" ones. 

> # For UHCI controllers, either "modprobe usb-uhci" OR  "modprobe uhci". They are equivalent, but one might work better for you than the other.
# For OHCI controllers, "modprobe usb-ohci". 
# If these modules don't exist, it's possible that USB is built into your kernel. Also, on 2.6 kernels, the drivers are called uhci-hcd and ohci-hcd.
It doesnt say to do this but when i attempted to run **modprobe** on **ohci-hcd** it returns this error which may be important it may not: 
> FATAL: Error inserting ohci_hcd (/lib/modules/2.6.15-27-386/kernel/drivers/usb/host/ohci-hcd.ko): Operation not permitted

For the next step i browsed to  **/proc/bus/usb/devices** where the file was there but contained no data, again the tutorial claims this is not an issue. When i then run **demesg** it returns i huge list and ive pasted all that mention OV511 

around half way down:
> [17179620.464000] drivers/usb/media/ov511/ov511.c: Sensor is an OV6630AE
[17179620.692000] drivers/usb/media/ov511/ov511.c: Device at usb-0000:00:10.0-1 registered to minor 0
[17179620.692000] usbcore: registered new driver ov511
[17179620.692000] drivers/usb/media/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver

then at the bottom:
> [17183058.372000] drivers/usb/media/ov511/ov511.c: No decompressor available 
[17183390.104000] drivers/usb/media/ov511/ov511.c: No decompressor available
[17184935.028000] drivers/usb/media/ov511/ov511.c: No decompressor available
[17184935.176000] drivers/usb/media/ov511/ov511.c: No decompressor available 
[17184935.316000] drivers/usb/media/ov511/ov511.c: No decompressor available
[17184935.460000] drivers/usb/media/ov511/ov511.c: No decompressor available
[17185000.308000] drivers/usb/media/ov511/ov511.c: No decompressor available 

which repeats for around 5x as many lines but im saving space..
When i check in for **/dev/video** i find i have **video** and **video0** (is this causing confusion?) they are both device nodes and later with cam programs i cant find a command/option to specify device. I then provided full access to both devices (to be sure) for all users. 

When i then downloaded Xawtv and Camstream and try and run them they return these errors:

Xawtv:
> root@tetherblood:/home/matt# sudo xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.15-27-386)
can't open /dev/video0: Function not implemented
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Function not implemented
v4l2: open /dev/video0: Function not implemented
v4l: open /dev/video0: Function not implemented
no video grabber device available
root@tetherblood:/home/matt#


Camstream:
> root@tetherblood:/home/matt# sudo camstream
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
CVideoDevice::ResetImagesRGB()
CVideoDevice::ResetImagesYUV()
root@tetherblood:/home/matt#


Camstream will then open but offer no devices in the dropdown menu. I hope someone can actually help me with this as i use the cam alot and i would like it to be one less thing to have to boot to windows for.
Also can anyone suggest (who has read this far lol) for the future any cams that work more seemlessly in Linux Ubuntu?

If you have read this far thanks and i hope someone can help ](*,) 

Matt

---

### Post by tetherblood on 2006-11-07
shameless bump

---

### Post by NicePics13 on 2007-02-11
I suspect your cam should work with the **gspca** driver (formerly known as **spca5xx**)
Available via apt-get.

---

### Post by FRuMMaGe on 2007-09-05
Same problem here.

Please help :(

---

