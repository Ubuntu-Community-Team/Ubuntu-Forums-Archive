---
title: "Low brightness + &quot;Unknown&quot; graphics driver in HP Mini 5102"
date: 2012-01-05
forum: Hardware
---

### Post by qgil on 2012-01-05
Hi, I just installed Edubuntu 11.10 in an HP Mini 5102 for my kids. Everything seems to work fine except the maximum brightness is too low.  fwiw I have got the same problem with the Ubuntu 10.* releases.

I have tried anything through the system settings UI and even some of the command line tweaks in the forum for user having problems with brightness in 11.10. The problem is not about display dimming alone or anything: it's just that the max brightness is far from the brightness this display is capable of offering (as seen in Windows).

System info > Graphics will report

> Driver Unknown
Experience Standard

lspci reports

> VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])
Subsystem: Hewlett Packard Company Device 3653
(...)
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

...

(((same for Display controller: access denied)))

...

Multimedia controller: Broadcom Corporation BCM70012 Video Decoder [Crystal HD] (rev01)
Subsystem: Broadcom Corporation Device 2612
...
Capabilities: <access denied>
Kernel driver in use: Broadcom 70012 Decoder
Kernel modules: crystalhd

Any help is appreciated. Thank you!

---

### Post by Mark Phelps on 2012-01-05
System info is known to be unreliable and according to the command you ran, it looks like you're running the INFAMOUS Intel 915 chipset -- which means the Intel drivers are already installed.

If they were not, you would be seeing a command line interface, not a desktop.

And don't go looking into Additional Drivers because they won't be offered there -- since they're already installed.

---

### Post by qgil on 2012-01-05
So I shouldn't bother about these "access denied" reported lspci?

And besides, is there any way to push the brightness beyond that 100% offered by the settings UI?

---

### Post by qgil on 2012-01-06
SOLVED! By coincidence & luck.

After trying everything on the command line unsuccessfully I rebooted, went to the BIOS menu to see if I could find anything. Pressed F3 to select an option... and the screen brightness made a little jump up (F3 is also the hotkey to increase brightness).

What a surprise! I put brightness to the max with F3, then booted normally. Now the min / max brightness works correctly.

How stupid is that? Anyway, problem solved.

---

