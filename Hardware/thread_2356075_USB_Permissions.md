---
title: "USB Permissions"
date: 2017-03-19
forum: Hardware
---

### Post by colonelpenguin on 2017-03-19
I have an issue that I have been struggling with for a very long time, and I was wondering if anyone could provide some information to get the issue solved.  I have 3 USB tuners that I use for TV, and a USB camera attached to the same computer.  I use the camera for Skype, but every time I start Skype it sees the tuners as potential video sources... interrupting any ongoing TV recordings causing them to stop.  I would like to get Skype setup such that it doesn't see the tuners.  I was thinking I might be able to handle this with permissions, but I am unsure how to accomplish this.  Any ideas?  Thanks in advance for considering how I might solve this issue!

---

### Post by TheFu on 2017-03-20
Don't know the answer, but I suspect you'd want to force the device names to be explicit using udev rules.  That way, the order that each device is found isn't what determines the name, rather, the USB-ID (as shown by lsusb) will tie each USB device to specific device names in /dev/.

Make sense?

Start by mapping the USB-id output to device names.  Which is video1, video2 and video0?  Are they always named the same? What happens if 1 isn't plugged in? Do all the names shift?  I only run LTS releases and how devices get named drastically changed between 14.04 and 16.04. What release are you running?

Or, another option - you could remove the USB tuners (switching to network-based tuners like HD-Homerun models) so there is only 1 video camera, thus removing the confusion. Not ideal, but HDHR network tuners allow any computing device to use DLNA and watch TV - smartphones, tablets, Kodi/xbmc, plex and vlc clients.  Also, thanks to the REST interface for the HDHRs, recording TV becomes a timed wget command just to save the file. A raspberry-pi can do that, even for high-def channels.

---

