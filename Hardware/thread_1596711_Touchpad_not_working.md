---
title: "Touchpad not working"
date: 2010-10-14
forum: Hardware
---

### Post by schaefer007 on 2010-10-14
[FONT=Tahoma]Hi all,

I am using an Acer Extensa 5620 laptop and have Windows Vista and Ubuntu 10.04 installed on my machine. After a few days of running on Linux my touchpad stopped working. I'm new to Linux and have installed some misc applications here and there and am not sure if any of them could have caused the problem.

I have searched for a fix to the problem but can not fix it. The message I get is:

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

So, I searched the Filesystem for xorg.conf and the results are:

/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz

From my searches, I have read that I need to modify the xorg.conf file but from what I have seen I can't find it?

For the time being I am using a USB mouse but I prefer the touchpad.
Any and all help is appreciated.

Chris
[/FONT]

---

