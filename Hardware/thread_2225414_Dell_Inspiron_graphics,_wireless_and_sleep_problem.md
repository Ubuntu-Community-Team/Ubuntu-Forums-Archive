---
title: "Dell Inspiron: graphics, wireless and sleep problems"
date: 2014-05-21
forum: Hardware
---

### Post by temp23 on 2014-05-21
Hello!

I have a Dell Inspiron 8100 portable computer to which I have installed Ubuntu Linux version 12.04. The installation ran smoothly but there remain problems I'd like to solve.

First, it has a network (wifi) PCMCIA device plugged in: D-Link Air DWL-650. Its light labeled “act” is on, the other stays off. Ubuntu says this device is deactivated, but I can't understand why (there's no clear explanation like “Driver not found”, the device is just ignored).

There's also a graphics card problem. Whenever I plug an external screen (there's a VGA plug for that), I can see the desktop's wallpaper (only it, no icon, menubar, etc.) for the first couple of seconds and then garbage lines start to appear from the top to the bottom of both screens (force shutdown is the only thing to do then); it obviously looks like a driver problem, but I haven't been able to solve it, after hours of attempts. I've found the driver that looks like the good one (it's a GeForce 2, the driver is in a legacy list); when I try to install it (booting Linux in console-only mode being required for that), the install program reports 3 errors (and aborts after the third):
1: "WARNING: Skipping the runlevel check (the utility 'runlevel' failed to run)." (I think that one is irrelevant)
2: "The distribution-provided pre-install script failed! Continue installation anyway?" [yes|no]
3: "ERROR: The kernel header file '/lib/modules/3.11.0-19-generic/build/include/linux/version.h' does not exist. The most likely reason for this is that the kernel source files in '/lib/modules/3.11.0-19-generic/build' have not been configured."
I followed advices, searching with Google, to install some Linux SDK files (and others) but nothing changed.

Finally, I can't put the computer to sleep. Closing the lid or otherwise choosing a sleep option initiates the sleep process but stays running; the screen stays all white (even when closed). Waking the computer up, the screen turns into a checkerboard-like background and hard-shut down is the only option. To fix this problem, I think installing the graphics card's driver may be enough, though.

I already tried upgrading to Ubuntu 12.10, but the installer said my graphics card would [probably] not be supported; continuing anyway led to an unusable system (screen staying black after the Ubuntu logo shows upon starting up) and I had to reinstall 12.04.

Any suggestion or comment would be greatly appreciated.

---

