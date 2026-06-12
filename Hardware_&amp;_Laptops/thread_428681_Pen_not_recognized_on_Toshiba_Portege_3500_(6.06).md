---
title: "Pen not recognized on Toshiba Portege 3500 (6.06)"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by emdalton on 2007-04-30
Hi folks,

Ubuntu 6.06 installed without trouble on the Toshiba Portege 3500 from the Toshiba USB CDROM drive. Everything works fine using the touchpad. However, I am unable to get the system to take any input from the stylus (which is the whole point of trying to install on a tablet, really!) The stylus was working under windows, so it's not a hardware problem per se. What I've done so far:

Installed wacom-tools package (and a required dependency, setserial) per [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

Edited /etc/X11/xorg.conf per the post in [http://ubuntuforums.org/showthread.php?t=120369](http://ubuntuforums.org/showthread.php?t=120369) (my xorg.conf matches [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting))

Tried manually setting the IO address using "setserial /dev/ttyS0 port 0x338 irq 4 autoconfig" per a suggestion at [http://www.eklhq.com/3500/old/index.html](http://www.eklhq.com/3500/old/index.html)

I rebooted between each of these steps and tested, and no luck. dmesg |grep wacom returns nothing.

I tried sudo wacdump /dev/input/event2 and /dev/input/event3 and I don't know what I'm supposed to be looking for, but since a lot of fields are filled in with "unknown", "0.00" or are blank, I'm guessing this isn't what I'm supposed to be seeing.

I have over a decade of experience with unix (Solaris), but I've only been experimenting with linux for a few months, and this is my first attempt to get a tablet working. Can anyone direct me to resources that can explain how I can troubleshoot -- and hopefully correct -- this problem?

Thanks!

---

### Post by jharbert on 2007-04-30
Try the instructions on [this thread]("http://ubuntuforums.org/showthread.php?t=184542").  That's how I set it up at first.  For other tablet related information check out this [howto]("http://ubuntuforums.org/showthread.php?t=371510").

---

### Post by emdalton on 2007-05-01
Thanks! That was just what I needed. The GIMP works great!

---

