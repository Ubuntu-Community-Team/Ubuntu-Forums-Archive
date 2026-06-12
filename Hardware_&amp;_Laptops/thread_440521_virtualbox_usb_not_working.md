---
title: "virtualbox usb not working"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by Bashed on 2007-05-11
I've installed virtualbox today and created an XP disk. 

I've enabled usb controller via the VD settings and it shows "7 active", however none work  through the XP virtual disk

It gives this error if I click on the usb icon at the bottom right and select any usb device such as my tv tuner or sound card


Not permitted to open the USB device, check usbfs options.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by nightfrost on 2007-05-13
I added this to /etc/fstab

```
# usbfs
none    /proc/bus/usb   usbfs   devgid=1001,devmode=664 0       0

```

which gives read/write permissions to users in group 1001 (vboxusers), which I assume your user is a member of. I'm not sure where ubuntu actually mounts usbfs, but this seems to work for me.

Perhaps one should file a bug report, feature requesting changes that makes ubuntu play nicely with virtualbox. A USB group out of the box wouldn't hurt...

---

### Post by El Viejo Lobo on 2007-05-17
> **TalkJesus said:**
> I've installed virtualbox today and created an XP disk. 

I've enabled usb controller via the VD settings and it shows "7 active", however none work  through the XP virtual disk

It gives this error if I click on the usb icon at the bottom right and select any usb device such as my tv tuner or sound card


Not permitted to open the USB device, check usbfs options.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I installed Virtualbox on Feisty and created XP disk too.  The USB for my printer and mouse works perfectly - The mouse worked automatically on install and the printer was installed like we do in Windows. The problem is with the USB connection that I use for my Webcam (Logitech) and the USB Memory Stick. I do not think that it as to do with Ubuntu. First of all we are dealing with a different machine that have to recognize the USB device. Second, I do see my memory stick in the Ubuntu bar and if I full it out I got the Ubuntu telling me that it was unsafe  to eject the M.Stick.
I think that the problem is, how to make Windows in VM to recognize the USB connection that is ignored, Who knows the answer? Please HELP!:confused:
:lolflag:

---

### Post by El Viejo Lobo on 2007-05-17
> **TalkJesus said:**
> I've installed virtualbox today and created an XP disk. 

I've enabled usb controller via the VD settings and it shows "7 active", however none work  through the XP virtual disk

It gives this error if I click on the usb icon at the bottom right and select any usb device such as my tv tuner or sound card


Not permitted to open the USB device, check usbfs options.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

You may try this.

[http://ubuntuforums.org/showthread.php?p=2674013#post2674013](http://ubuntuforums.org/showthread.php?p=2674013#post2674013)

---

### Post by El Viejo Lobo on 2007-05-17
Hi! happiness was short. USB Memory Stick is OK - Webcam went dead after first time.  I can not find the Webcam anymore.   How to get it working? Please.:confused:

---

