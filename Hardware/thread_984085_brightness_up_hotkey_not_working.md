---
title: "brightness up hotkey not working"
date: 2008-11-16
forum: Hardware
---

### Post by arnohr on 2008-11-16
Hey guys!

Last Saturday I got my brandnew Lenovo Thinkpad SL500 NRJ9AGE and I installed Ubuntu Intrepid Ibex (8.10) 64bit.
The problems concerning the hotkeys are still up2date for this modell. I read that with hotkey-setup 0.1.28ubuntu7 the problems should be fixed, but unfortunately not for SL500.

The main problem is the brightness of the display. The hotkeys works very bad if I try to change the brightness.
The first thing is, that the function is inverted. The second point, the procedure of changing the brightness is very inaccurate. The background gets dark an returns than in an brighter or smother light. Its a very strong flickering of the display.

If I disconnect AC, the display gets on battery brighter and returning to AC it gets darker again. Cazy thing... Also when I log into Ubuntu with my user. First in the gdm, the display is shining like the sun. After I logged it gets darker again... GRML!!!

I tested following keys:

Key:         Works?
------------------------------------------------
Lock Screen     = no
Battery status     = no
Sleep         = yes
Wifi/RF kill     = no
Switch displays = yes
Hibernate     = no (but I use a encrypted swap-partition)
Brightness up     = yes, but inverted
Brightness down = yes, but inverted
Volume up     = no
Volume down     = no
Mute         = no
Multimedia Keys = no
Display Zoom     = no

The are additional problems with the fingerprint sensor and the webcam. They dont work, but I think thats another construction side.

An additional hint:
If I do "sudo modprobe tinkpad_acpi", I get this message:

FATAL: Error inserting thinkpad_acpi
(/lib/modules/2.6.27-7-generic/kernel/drivers/misc/thinkpad_acpi.ko): No
such device

I would be so glad, if some can get me some advice. Its not very funny, if your brand new toy will not work in top condition.

Greetings!
Arnohr

---

### Post by arnohr on 2008-11-16
I think, I found the reason in the Thinkpad Linux Mailinglist:

[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-October/044992.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-October/044992.html)

The firmware is incompatible to the thinkpad_acpi module.

---

### Post by tubbygweilo on 2008-12-13
Same problem with me, most annoying to me it seemed that the FN 11 and FN 12 were connected incorrectly, strangely enough things are now working. This happened after a couple of reboots and the application of the the Nivida restricted drivers.
[http://ubuntuforums.org/showpost.php?p=6358117&postcount=376](http://ubuntuforums.org/showpost.php?p=6358117&postcount=376)

---

