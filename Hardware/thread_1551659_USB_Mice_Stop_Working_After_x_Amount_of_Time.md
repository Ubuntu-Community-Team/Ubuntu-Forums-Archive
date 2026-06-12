---
title: "USB Mice Stop Working After x Amount of Time"
date: 2010-08-12
forum: Hardware
---

### Post by soggydoggy on 2010-08-12
Hi all,
Got a strange one that I haven't had a problem with before in that USB mice stop working after a certain amount of time. They just do not respond at all.
This is with 3 different mice, Microsoft, Trust and Logitech - makes no difference.
The weird thing is, when it happens and I do "lsusb", the mouse will be listed. If I remove the mouse and do "lsusb" again, it still shows as being connected!
If I boot the computer up with no mouse attached, then plug it in once Ubuntu has loaded, it works absolutely fine and never stops working. It also recognises when it has been unplugged and plugged back in correctly.

It's almost like whatever detects devices on bootup, say HAL for example, is conflicting with the other module that detects hotplugged devices, perhaps evdev.

Now this also happens with my network card. After a few hours my network card will stop working (not tied in with the mouse stopping). If I take my ethernet cable and plug it into my spare NIC, everything works! So it's like turning off 1 NIC and activating the other randomly... bizarre.

I wonder if this is a bug with evdev or HAL or something, but have no idea how to fix it and it is really getting on my nerves now.

I have no problems with previous versions of Ubuntu, or other Distros.

Currently running 10.04, but the bug happens in the Alpha of 10.10 too (presumably because it is based on 10.04).


uname -a output: Linux *****-desktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

---

