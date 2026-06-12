---
title: "Toshiba Portege M400 - Screen Rotate not working right"
date: 2011-06-02
forum: Hardware
---

### Post by practic on 2011-06-02
I recently picked up a few used Toshiba Portege M400 tablet-notebooks. They are quite nice, and the default system was Windows XP. I added Natty to them also (dual-boot).

My son's machine came with the default screen 1024x768. Mine came with a hi-res alternative, 1400x1050...but they are both 12" (same physical size).

Under Windows, if you swivel the screen and lay it flat over the keyboard (like a tablet) it automatically rotates into portrait mode. Ubuntu doesn't do that, but there is an article on getting it to work via shortcut.

[http://wiki.control-d.com/index.php?title=Ubuntu_Intrepid_Ibex_%288.10%29_on_a_Toshiba_Protege_M400]("http://wiki.control-d.com/index.php?title=Ubuntu_Intrepid_Ibex_%288.10%29_on_a_Toshiba_Protege_M400")

The article is dealing with Ubuntu 8.10, so the stuff about adding entries to xorg.conf no longer applies (I've tried it with and without, it makes no difference).

The problem is, when I rotate the screen to Portrait on the notebook with the hi-res screen, I end up with a black bar, about 2" high, going from the top panel down. If I drag a window into this area, it disappears under the black patch. It seems to be a problem with XRandR. If I switch to 1024x768, it works fine. Yet 1400x1050 is the native res for this screen. So, I think X is not realizing that it is dealing with that kind of screen and is defaulting to 1024x768, hence the black patch of non-accessible screen real estate.

I've attached a screenshot.

Anyone think this is fixable via script or setting? Or is it a limitation in the xserver? 

By the way, it is using Intel 945 video...

---

### Post by ibbuntu on 2011-06-06
I'm having the same problem with my Portege R400, this was working fine with Ubuntu 10.10, it seems to be a bug with 11.04. I haven't found a bug report for this yet.

---

### Post by practic on 2011-06-06
I could file a bug, but what do I file it under?

---

### Post by ibbuntu on 2011-06-06
I would probably suggest xorg-xserver, that should get it looked at by the right people. If it turns out to be then wrong package it can be assigned to the right package later. Ill also file a bug as it's suggested that for x problems a separate bug should be reported for different hardware.

---

### Post by ibbuntu on 2011-06-06
Ok I've reported the bug for my hardware #793764 on launchpad under the 'xorg' package, by running 'ubuntu-bug xorg' from a terminal.

---

### Post by practic on 2011-06-06
Oh, I didn't know you could do that from the terminal.

I've added a comment to your bug report. Here's the link in case anyone else wants to subscribe to it:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/793764]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/793764")

---

