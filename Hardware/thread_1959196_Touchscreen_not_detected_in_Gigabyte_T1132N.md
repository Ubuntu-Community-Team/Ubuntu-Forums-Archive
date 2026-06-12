---
title: "Touchscreen not detected in Gigabyte T1132N"
date: 2012-04-15
forum: Hardware
---

### Post by pommessemmel on 2012-04-15
I have Kubuntu oneiric 11.10 (3.0.0-17 64bit kernel) running on a  Gigabyte T1132N. Unfortunately the capacitive multi-touch screen from  'cando' is not recognized by the kernel. 

In windows 7 the screen works and is listed with the following parameters:

Gigabyte MultiTouchPanel with Controller
Port_#0006.Hub_#0004
USB\VID_2087&PID_0B03&ReV_0204
USB\Class_03&SubClass_00&Prot_00\Device\USBPDO-7
oem42.inf:MST_HID.NTamd64:HIDSelSusp1.NT.6.0:7.0.0.0:usb\vid_2087&pid_0b03

The vendor id reveals that this device is from a company named 'cando'

In linux neither 'lsusb -v' nor 'lspci -nn' nor 'lsinput' nor 'lshw -numeric' lists anything with the desired id. 

Tweaking and updating the bios didn't change anything. 
Running another kernel didn't change anything.

[COLOR=White]touchscreen, touch-screen, touch screen, not found, not recognized, not detected, not present, cando, gigabyte, T1132N, 2087, 0b03[/COLOR]

---

### Post by Ray-Ven on 2012-05-12
same in precise. Is there any Progress?
Should we post a bugreport?

Windows says it's a:
gigabyte multitouch panel with controller
or
Cando-Capacitive Touch Screen

---

### Post by Ray-Ven on 2012-05-12
[http://ubuntuforums.org/showthread.php?t=1483973&page=2](http://ubuntuforums.org/showthread.php?t=1483973&page=2)
looks interesting
Probably the device is working with:

```
dev/input/event5
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event6
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

```

[http://ubuntuforums.org/showthread.php?t=1375047](http://ubuntuforums.org/showthread.php?t=1375047)
interesting too.
maybe hidtouch does the trick?

---

### Post by pommessemmel on 2012-05-12
no success thus far, although I tried a lot

I suspect it's not a driver problem because a suitable driver exists (hidtouch didn't solve the problem). Looks more like the touchscreen does not answer on the enumeration command of the usb host controller but I am not totally sure about this. A test with USBlyzer under windows suggests it might be a power management issue.
I also switched to precise recently which didn't resolve the problem.

---

### Post by pommessemmel on 2012-05-24
I found one way to activate the touch screen:

- On computer start press F2 to enter the BIOS setup

- under Main set 'User SETUP Options' to 'advanced'

- under Advanced go to Onboard Device Configuration and set 'SmartCharge' to 'Always Off'


I assume that changing that option lessens the power efficiency of the computer.
Windows 7 is still able to use the touch screen with the 'SmartCharge' enabled and linux and other windows versions don't.

---

