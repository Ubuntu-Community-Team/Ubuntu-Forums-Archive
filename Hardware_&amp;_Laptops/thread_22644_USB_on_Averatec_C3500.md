---
title: "USB on Averatec C3500"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by Plank117 on 2005-03-28
I've been running Ubuntu on this laptop for about a month and just about everything works, except for the touchscreen, Wi-Fi, and usb. My problem is that linux isn't seeing any of my usb devices, when I have a plug and play usb mouse connected and a usb flashdrive. Has anyone else had this problem? <Edit: I checked in /proc/bus/usb and there wasn't anything in there>

---

### Post by joseph.brower on 2006-08-09
> **Plank117 said:**
> I've been running Ubuntu on this laptop for about a month and just about everything works, except for the touchscreen, Wi-Fi, and usb. My problem is that linux isn't seeing any of my usb devices, when I have a plug and play usb mouse connected and a usb flashdrive. Has anyone else had this problem? <Edit: I checked in /proc/bus/usb and there wasn't anything in there>

From my research, I've found that the newers BIOS for that laptop causes that issue.  I'm working on getting Averatec to get me the old Bios so that I can flash it back to the old version.  From what I've seen, that corrects the USB and PCMCIA.  The wireless should work out of the box because it is a ralink.

---

