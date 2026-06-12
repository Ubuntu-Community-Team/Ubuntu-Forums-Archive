---
title: "USB devices do not re-connect after suspend (9.10)"
date: 2009-11-03
forum: Hardware
---

### Post by CorporateGoth on 2009-11-03
I have a Thinkpad T60p, and it has several "usb" devices built in.  These include a fingerprint reader and my Sierra Wireless (ie. 3G modem) card.

After I suspend the laptop, and resume (which works fine), these devices are disconnected, and I don't know how to reconnect them.  I can "reconnect" the Sierra Wireless card by simply flipping the switch to disable all wireless devices (wifi, bluetooth and 3G), and then flipping it back on again.  This works.  I don't know what to do about the fingerprint reader.

I even tried doing:
rmmod sierra usbserial
modprobe sierra

This does not reset the device, I have to "unplug" it (by flipping the switch) and "plug" it in again.

This is probably related to [this post]("http://ubuntuforums.org/showthread.php?t=1017907") about the touchpad (I disabled the touchpad on my laptop, I hate touch pads).

This all worked perfectly on 9.04 (ie. before upgrade).

---

### Post by CorporateGoth on 2009-11-03
Bump.  This is a REALLY annoying problem, anyone have any ideas where to look or workarounds?

---

### Post by birdy on 2009-11-03
Yep, I have the same issue. It is being dealt with [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352"), I hope.

---

### Post by CorporateGoth on 2009-11-03
Actually my issue is [Bug #405053]("https://bugs.launchpad.net/ubuntu/+bug/405053").

And the workaround listed in that bug also works for me.

I found out it's only the sierra wireless card that is being 'rfkill' blocked on resume.  The fingerprint reader problem seems to be that for some reason the thinkfinger pam configuration got reverted (I just enabled it again and my fingerprint reader works just fine).

---

