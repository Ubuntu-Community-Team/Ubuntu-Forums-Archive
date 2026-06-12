---
title: "Can not extract pictures from the SD of a Fuji F300EXR"
date: 2012-05-27
forum: Hardware
---

### Post by altella on 2012-05-27
I have a Fujifilm F300EXR camera. 
In configuration -> remavable devices -> cameras. I have selected "Import digital pictures when connected".
Xfce recognizes the camera when I plug it to the USB port, and launches Thunar, but the SD memory of the camera does not appear anywhere, and I can not access to the photos to copy them.
Using F-Spot, I obtain that there is not a device connected.
Finally running lsusb, the fuji appears.

How can I make the memory visible to copy and extract photographs???

Response from lsusb:

lsalberto@alberto-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
**Bus 001 Device 004: ID 04cb:0225 Fuji Photo Film Co., Ltd **

thank you all,

---

### Post by efflandt on 2012-05-27
The last time I connected a still camera directly to a computer, the camera and computer had serial ports (before USB - slow).

Have you tried  a memory card reader?  That is more universal as usb mass storage, and should automount like USB  flash memory or drive.

---

### Post by altella on 2012-05-28
Yes, It works with the SC card adapter...
My question waas related to the fact that until now it has worked in Ubuntu with no problems and with Xfce it does not.
It is detected, but it is impossible to read the SD card with Thunar for example.
My doubt is more about why in Ubuntu yes and in Xcfe no. THe core system and libraries are not the same?

Thank you,

---

### Post by altella on 2012-05-28
Anyway, taking in to account the output of lsusb, how could I mount the device listed?
With my smartphone happens the same as with the camera, and its microSD is not accesible, I do not want to open and dismount the smartphone everytime I want to extract a picture or video !!!

Any advise?

Thank you all...

---

### Post by altella on 2012-05-31
Finally, I have discovered that Xubuntu with Xfce, only mounts drives that are "masive Storage" devices. I have configured my smartphone to be seen that way and it is mounted. My Fuji F300EXR, unfortunately does not have that massive storage mode.

My question still is: If the core system is the same and the only thing that changes is the graphics, Why Ubuntu mounts these devices and Xubuntu does not?

Thank you for all the responses.

---

### Post by Jose Catre-Vandis on 2012-06-01
what does 
```
sudo fdisk -l
``` give you? Does it recognise a device associated with your camera?

---

### Post by LewisTM on 2012-06-01
Did Ubuntu open Nautilus or some other program when connecting the camera?

My guess is that your camera was using a vendor-specific protocol or the Picture Transfer Protocol (PTP). This his handled by the gphoto2 library and can be used by programs like GThumb or Shotwell.

You can set Thunar Volume Management to open such a program when a camera of that kind is detected. Same as in GNOME but it is set to "Ask what to do" instead of Xfce's default "Do nothing".

If you want to physically mount a gphoto device you can take a look at the gphotofs pakcage but since you can enable mass storage mode that won't be necessary.

Cheers!

---

### Post by altella on 2012-06-03
with
 sudo fdisk -l 
I obtain information of the hard Disks mounted in my PC, the camera does not appear.

I have also installed gphoto2 library and I obtain the same results, the camera is detected but it is not mounted.
With previous versions of Ubuntu (10.04) the camera waas detected, mounted and Nautilus was launched.

Thank you,

---

### Post by LewisTM on 2012-06-03
Install gThumb and use this command in the Camera section of  'Removable Drives and Media' ([FONT="Courier New"]thunar-volman --configure[/FONT])
```
sh -c "gvfs-mount -d %d; gthumb --import-photos %d"
```

---

