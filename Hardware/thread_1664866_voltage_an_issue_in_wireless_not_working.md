---
title: "voltage an issue in wireless not working?"
date: 2011-01-11
forum: Hardware
---

### Post by jdoggsc on 2011-01-11
Hi, I have an HP with a broadcom wireless chip.  I have had this laptop for a year and the wireless has always worked in both linux and win7 until recently.  now, it absolutely does not work in linux, but it WILL work in windows 7 after I use the hardware switch to disable wireless and then reenable it.

Linux still recognizes my wireless.  doing lspci shows that it DOES exist.  linux still lists it as a device (eth1).  I even reinstalled ubuntu last week and reinstalled the proprietary broadcom driver, which has always worked for me perfectly. still no luck.

there's a noticable difference in how linux and windows both use my hardware:
--I can suspend and hibernate in ubuntu with no problems
---I can suspend in windows but it wakes up if i close the lid, and sometimes wakes up by itself even with the lid open.
---windows freezes every time i hibernate (i don't know what this means)
--I can't see any wireless networks in linux
---I CAN see wireless in windows

I'm thinking windows is managing the hardware by sending higher voltage to certain components.  that is why the touch-pad and touch pads for volume adjustment will wake the lappy in windows, but not linux.  I'm thinking windows is sending higher voltage to the wireless as well, but the voltage linux sends is not high enough to make the aging components in my laptop work anymore.

I'm no EE, so I don't know if this is even a valid hypothesis, but what are your thoughts?   Is there even any way of bumping up power to some components in linux? or is that way too deep in the machine code to change?

---

### Post by jdoggsc on 2011-01-18
bump

---

