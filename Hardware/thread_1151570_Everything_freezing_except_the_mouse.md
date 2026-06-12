---
title: "Everything freezing except the mouse"
date: 2009-05-07
forum: Hardware
---

### Post by JHumphrey on 2009-05-07
I just installed 9.04 through wubi, and when I start up and open some type of program, everything freezes, except for the mouse, which, when moved, updates about every second or so. ctrl-alt-f1 does nothing, and to restart, I had to hard shutdown.

I am on a Gateway Tablet Laptop. I have an ATI x1400 gfx card. I checked out xorg.conf, and nothing was mentioned about wacom.

Have any ideas on what could be wrong?

---

### Post by Favux on 2009-05-07
Hi JHumphrey,

Two possibilities come to mind.

ATI dropped support for the X1400 in the Catalyst for Jaunty (the proprietary "fglrx" driver) so you have to use Xorg.'s "radeon" (or maybe "radeonhd").

Wacom in Jaunty now uses the HAL/.fdi method not xorg.conf.  So you need to remove your Wacom entries, especially in "ServerLayout".  It's not clear to me if the Wacom entries breaking X is an expected behavior or not.  I think it is a bug because I've seen a launchpad report with a patched Xorg-xserver that seems to eliminate the breakage.

---

### Post by hagantic42 on 2009-05-07
I don't think is that driver. I have a Logitech G5 mouse and a hp dv8000 with the Centrino Duo processor and when ever I plug in the mouse this go wonky. By this I mean that the courser itself moves just fine but there are jumps and lags in the click response. A friend of mine that is well versed in linux thinks it may be an issue with the usb handling system. Also I know its the mouse considering all programs become instantly responsive again once I unplug the mouse, also the mouse in windows works flawlessly.

---

### Post by pro003 on 2009-05-07
> **hagantic42 said:**
> I don't think is that driver. I have a Logitech G5 mouse and a hp dv8000 with the Centrino Duo processor and when ever I plug in the mouse this go wonky. By this I mean that the courser itself moves just fine but there are jumps and lags in the click response. A friend of mine that is well versed in linux thinks it may be an issue with the usb handling system. Also I know its the mouse considering all programs become instantly responsive again once I unplug the mouse, also the mouse in windows works flawlessly.

Did you install / enable compiz...? And if you did, that may cause this behavior, I've seen it myself recently.

---

### Post by JHumphrey on 2009-05-07
Interesting replies.

I do have a g5 mouse plugged in. 

Also, this freezing happened the first time i logged in, so I doubt it is compiz.

I'll check out the radeon and g5 issues though. 

Thanks

---

### Post by pro003 on 2009-05-07
this could be related to hardware issues also, your graphic card perhaps... try to uninstall the video driver and see if there's any difference.

---

