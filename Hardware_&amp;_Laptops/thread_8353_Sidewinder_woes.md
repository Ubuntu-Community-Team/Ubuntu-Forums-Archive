---
title: "Sidewinder woes"
date: 2004-12-16
forum: Hardware &amp; Laptops
---

### Post by zneastman on 2004-12-16
While I've managed to get my old MS sidewinder working under other distros -- just by loading the "gameport" and "sidewinder" modules -- I can't seem to get it going with an up-to-date Warty.  Here's what I've found so far:

1]  My gameport is autodetected, but the sidewinder isn't.  Under other distros (like SuSE or KnoppiXMAME) both are.  

2]  The "sidewinder" module loads, but doesn't create any device nodes under /dev/input/ or /dev.  I can likewise load the "joydev" module, but it doesn't create device nodes.

3]  "MAKEDEV js" gets me the js and djs nodes if I run it in /dev/input/, but those nodes don't seem to map to any real devices -- even when the sidewinder module is loaded.  For instance, if I "cat /dev/input/js0" I get a "no such device" error.  Ditto js1, djs1, etc., excepting djs0, which apparently maps to my mouse. 

In other words, the gameport and sidewinder both appear to be working correctly, and there exist 2.6.xx kernels that deal with the hardware I'm using -- or, while this may be a kernel-level problem in which the sidewinder and joydev modules aren't creating device nodes, it seems endemic to Warty's current kernel build.  (I've not tried to use it under a different Warty kernel, nor to build my own.)  Second, even if the module isn't creating nodes, the sidewinder should be autodetected -- a distinct, but possibly related, issue.

So:  A look around the forums suggests that at least one person has gotten his sidewinder to work.  If you have, how did you do it, and which kernel build are you using?  Was it autodetected, or did you have to load the module (or make the device nodes) yourself?   

Also, does anyone have any suggestions for how to get the sidewinder to work, or better define the problem?  Donkey Kong loses something when played with the keyboard.

---

### Post by ibbuntu on 2007-09-19
I am having this problem now with Gutsy. I've tried all the tips I can find for getting my sidewinder joystick to work, but still no luck. This seems to be a very old issue, will there ever be a fix for this?

---

### Post by stijngysemans on 2007-12-15
I also have this problem.

---

### Post by thane1 on 2007-12-21
Me also...  Have just gotten Doom3 to run in Ubuntu 7.10 through zerowing.idsoftware but I cannot get my Sidewinder Dualstrike controller to work.  In fact I don't see any place in the game menu systems, which even addresses the possibility of using it.  In Preferences - Hardware Information - Device Manager, I can see the controller.  But I don't know if its actually enabled.  Some time ago I had the Dualstrike working with I think it was Dapper.

---

### Post by thane1 on 2007-12-22
Have been doing a bit of searching and as I previously stated, I can see a listing for the controller in System-Preferences-DeviceManager.  Looking in /dev/input/by_id I also have 2 listings for /dev/input/by-id/usb-Microsoft_SideWinder_Dual_Strike_USB_version_1.0-event-joystick .  One has a link target of /dev/input/event2 and the other has a link target of /dev/input/js0 .  If I look in my /etc/X11/xorg.conf file, I would have suspected I'd find a reference to the Dualstrike under a "Section InputDevice" heading.  No luck there.  I would imagine there should be a reference in this file to a js0 controller having somewhere in the neighbourhood of 15 to 17 buttons (but I could very possibly be way off base on this).  This is about as far as I can go on my own, as I'm at a loss of what I might be able to add to my xorg.conf file if this is in fact required at all.  I have edited this file in past versions of Ubuntu to change monitor settings.  So I'm not averse to giving it a go, if I know what I should be trying.  Does anyone have an entry in their xorg.conf file referring to the controller?

---

### Post by tgalati4 on 2007-12-22
When you were using a working distro (like SUSE) did you print out your xorg.conf to see what the settings were?  Perhaps you can transfer them.

---

