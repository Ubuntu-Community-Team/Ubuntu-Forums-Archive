---
title: "USB ports randomly turning off"
date: 2012-04-09
forum: Hardware
---

### Post by M1NDF1R3 on 2012-04-09
Has anyone else come across a very annoying issue with there usb ports on a laptop where the ports themselves seem to randomly turn off? 

Ive been getting this for some time now, When this happens My Wifi icon changes to the disconnected icon and the only way i can get my connection back is by doing a full reboot.

Now i know this is not an issue with my dongle as if i happen to have my iphone connected when the usb terminates, it crashes my iphone, if any other usb device is plugged in they simply do not show up as being connected, so again i have to reboot my machine to see them again.

What is going on?

---

### Post by foresthill on 2012-04-10
Running 10.10 here and having same problem. My CDMA modem shuts down randomly. I don't think it's the provider, because the device disappears, then comes back a minute or so later. 

Could be a hardware problem with the modem itself, but I'm more inclined to think that Ubuntu is dropping USB devices from time to time. It's more noticeable with my modem because it needs to "flip" when it gets disconnected and takes 30 seconds or so to get re-recognized. Very annoying.

I believe my USB mouse and keyboard have done this too.

Running a Gateway notebook with Intel chipset.

---

### Post by foresthill on 2012-04-10
No answer? This is a really serious bug, even worse than the dead backlight while installing and black screen on wake up from suspend (neither of which ever got fixed, after almost a year since they were reported). 

[http://ubuntuforums.org/showthread.php?t=1741556](http://ubuntuforums.org/showthread.php?t=1741556)

Is there anyone working to fix this OS? Sometimes I seriously wonder.  :-(    :-(    :-(

---

### Post by kiirokurisu on 2012-04-10
It could be a power management bug affecting your specific chipset. USB selective suspend turns of USB devices when they are perceived by the kernel as being idle, however it doesn't always work right.

[This page]("http://ubuntuforums.org/www.lesswatts.org/projects/devices-power-management/usb.php") explains how to enable and disable USB autosuspend.

---

