---
title: "wacom volito2: no device listed in xsetwacom"
date: 2008-11-14
forum: Hardware
---

### Post by didi32 on 2008-11-14
Hi,

I have a Wacom Volito 2 tablet and Ubuntu 8.10. The tablet does work probably but I use two screens and would like to assign the tablet to only one portion of my first screen. The problem is that the xsetwacom command does not return any device for my tablet:

john@ljf:~$ sudo xsetwacom list dev
john@ljf:~$ 

xdump -i will however show the following line:
Wacom Volito2 4x5              extension

and in my /dev/input folder I see the two following links:
tablet-volito24x5
and wacom

which target is event5, but using event5 as the dev name doesn't solve anything:
john@ljf:~$ sudo xsetwacom set event5 TopX -200
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'event5'


How can I set these parameters without the device listed or how can I get teh device to be listed?

Thanks a lot for your help,

---

### Post by didi32 on 2008-11-14
If I can't get an answer to my question here, do you know of any forum or website where I could ask this question and hope to get an answer? 

Thanks,

---

### Post by Jameshfisher on 2009-04-07
This was a while ago, but I just had the same issue and there's a simple fix:
The problem/confusion is that dev_name in xsetwacom help does NOT refer to a path to the device.  Hence neither /dev/input/wacom or /dev/input/eventX will do.
Rather it refers to the "identifiers" used in /etc/X11/xorg.conf.  If you set up your xorg.conf as instructed at [http://linuxwacom.sourceforge.net/index.php/howto/x11](http://linuxwacom.sourceforge.net/index.php/howto/x11) , and restart your X server, then xsetwacom should list the devices you include here.

---

