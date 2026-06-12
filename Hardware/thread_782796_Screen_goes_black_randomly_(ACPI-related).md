---
title: "Screen goes black randomly (ACPI-related)"
date: 2008-05-05
forum: Hardware
---

### Post by cornware-cjp on 2008-05-05
Hi,

When I close the lid of my laptop, and re-open it later, then the system seems to enter a state where everything seems to work normally, but at certain moments the screen goes black. Moving the mouse or touching a key turns it on again, but it's still very annoying. It's like a screensaver that activates while you're working on your computer. Actually, as long as I don't kill xscreensaver, the screen going black event also triggers xscreensaver to lock my screen.

Hardware:
HP Compaq nx6110 laptop
Intel 915GM video card

Software:
Xubuntu 8.04
Version history:
Kubuntu 5.10; Kubuntu 6.06; Xubuntu 6.06; Xubuntu 8.04

I tried to find the cause of this problem, and I think it is ACPI-related. I can reliably trigger the bug: the following command makes my screen go black:
```
cat /proc/acpi/thermal_zone/TZ3/temperature
```

But this is **only after** I closed the lid and opened it. As long as I keep the lid open continuously, there is no problem. Also, cat'ing other files in /proc/acpi doesn't seem to trigger the bug. I also had a look at the file /proc/acpi/button/lid/C1E5/state. Usually, this is the normal state:
```
state:      open
```

But in the "buggy state" after closing and re-opening the lid, the state is:
```
state:      closed
```

Also, acpi_listen and dmesg mention an interrupt from my video card at the same moment when my screen goes black. I don't know whether this is a cause or a result.

To me, it seems like the OS doesn't detect properly when the lid opens. Does anyone know how this can be solved? I didn't have this problem before upgrading to 8.04.

---

### Post by cornware-cjp on 2008-05-05
Update:

The problem seems to be the same as [this launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/159309"). However, I didn't find a solution for the problem, and apparently the problem still exists in 8.04.

---

### Post by khg1000 on 2011-04-27
I have not noticed this in 9.4 but it is real anoying in 9.10, 10.4, and 10.10. I thought it was a video clocking problem or a heat problem. I have noticed it right after I boot up but mostly after I have been doing something with flash player for a while.
 
Since then I have switched to xubuntu and it seems to not surface. I installed ubuntu and then loaded the xubuntu-desktop. 
 
My Laptops functional ability is not lost during the screen blink but it is hard to see what I am doing. Some times the screen will blink for about a half second at a time.

---

