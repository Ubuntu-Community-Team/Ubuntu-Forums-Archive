---
title: "Fans running at full speed constantly"
date: 2011-08-27
forum: Hardware
---

### Post by scottayy on 2011-08-27
Hey Guys,

Just did a fresh install of the latest ubuntu.  Everything was detected perfectly.  Only problem is my fans won't quiet down.  They're running at full speed all of the time.

I had a problem with this on windows too.. but using ASUS's AI Suite I could set the mode to auto and it would fix it.

Unfortunately I'm not very skilled in linux yet and I don't know how to control this.

How can I fix this and is there software I can download to tell me cpu temps and fan speeds (i like to know this even when it's not running full speed all of the time).

Motherboard: ASUS m4a88t-m/usb 3
CPU: AMD Phenom II x6 1055t

Thanks,
-Scott

EDIT|  I should mention that this is not a laptop.  It is a custom built desktop.  I thought I should post in here because it said "hardware", so please move if I posted in the wrong forum.  Thank you!

---

### Post by kyletstrand on 2011-08-28
There is a program called lm-sensors that you can use to control fan speed.

There's a nice easy tutorial you can read to set it up here:

[http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu)

Here is a more complete tutorial as well.  It's for Arch Linux, but it should still be applicable to Ubuntu.

[https://wiki.archlinux.org/index.php/Fan_Speed_Control](https://wiki.archlinux.org/index.php/Fan_Speed_Control)

Conky is a nice program to display all types of system info.  Installing is easy.  Simply open a terminal and type:

```
sudo apt-get install conky
```

For more info, here is a link to the Conky website:

[http://conky.sourceforge.net/](http://conky.sourceforge.net/) 

Hope that is helpful!

---

### Post by scottayy on 2011-08-28
Thanks a lot!  I'll have a play with those and see if I can't get something working.

---

