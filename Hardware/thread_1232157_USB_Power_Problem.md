---
title: "USB Power Problem"
date: 2009-08-05
forum: Hardware
---

### Post by Alan F on 2009-08-05
I have a Compaq nc4200 laptop which is dual booted with Win XP and Ubuntu 9.04. Also a separate HDD with Win 7 RC.

On both flavours of WIN and previous versions of Ubuntu (8.04 & 8.10) I have had no problems with USB devices (USB memory sticks and USB DVD drive)

With the current Ubuntu 9.04 the DVD drive seems to unmount at various random times and memory sticks seem reluctant to mount.

Checking in Device Manager I can see that these devices are flagged "Insufficient power to operate USB device".

In "USB EHCI Controller/Hub/Properties" I can see the entry "USB_device.max_power" is set to 0

Similarly in "USB EHCI Controller/Hub Interface/Properties" USB.max_power" is set to 0

This does not seem to be correct and is leading to any device being plugged in from being flagged "Insufficient Power"

Can anyone shed light on this and how it may be corrected?

---

### Post by jerrrys on 2009-08-05
looks like your going to need to look elsewhere.  my hub & hub interface are both set to zero.  i do not have any external devices to plug in except for a couple of flash drives.  never noticed it before or never checked it, but i also get an Insufficient Power warning on my flash drive.  why this warning is there i don't know, but not having any trouble with flash drives.   good luck...

---

### Post by breephd on 2009-08-09
did you figure this out? i am not sure what the person is saying when they say that they get an insufficient message on their flash drives, but yet they don't have a problem with them?  
 
it seems that ubuntu 9.04 has issues regarding the usb system.  for some reason it will not allow some devices to run and flags them and says "insufficient power"  maybe ubuntu 9.04 just doesn't liek some usb devices and it can't work with them, so it just says it's a power issue?

---

### Post by Alan F on 2009-08-09
No solution to this yet. Like you I believe that Ubuntu is not fully configuring the USB ports. Windows tells me that the internal Hub can deliver 500mA per port. Also when I plug in a memory stick it tells me that it is using 98-100mA.

Same hardware with Ubuntu just shows "Insufficient Power"

Is this because Ubuntu bMaxPower file is set to 0mA?

Memory sticks now seem OK (despite "Insufficient Power") but DVD still unmounts at random times. Is this responding to "Insufficient Power" state?

Is there a USB expert out there who can throw light on this?

---

### Post by teejcee on 2009-11-17
As I'm experiencing similar problems, I thought I'd bump this thead...

---

### Post by tbresson on 2010-06-21
Where do you find the error message?
I'm having problems with my external USB harddrive disappearing from the OS and I have to turn off the drive and reboot.
Simply rebooting gives me an error about the device not being ready.

I'm not 100% sure it's related to your issue but I thought it very well could be.

---

