---
title: "Need driver for HP w2007 20-inch LCD"
date: 2009-07-28
forum: Hardware
---

### Post by dennisbrain57 on 2009-07-28
Need driver for HP w2007 20" LCD monitor. By default Ubuntu does not support the recommended resolution of 1680 x 1050 @ 60 Hz

---

### Post by LowSky on 2009-07-28
it isn't that Ubuntu doesn't support the resoluitons its that the graphics driver does not support the resolutions...

do you know what chipset your graphics card uses? Intel, Nvidia, or ATI? Or something else?

---

### Post by dennisbrain57 on 2009-07-29
Computer is using Intel GMA 4500 chipset. 

Under Windows Vista 64-bit the Intel graphics drivers work perfectly with the HP w2007 monitor - looks great at 1680 x 1050 @ 60 Hz. 

Under Gnome 2.26.1 when I run System=>Prefs=>Display the only choices in the "resolution" dropdown list are the following:

1360 x 768 (16:9)
1152 x 864 (4:3)
1024 x 768 (4:3)
800 x 600 (4:3)
640 x 480 (4:3)

Can I edit a config file somewhere that will give me the choice 1680 x 1050?

Machine specs: Lenovo IdeaCentre K220 Model 5358-1FU
OS: Vista Home Premium 64-bit
CPU: Intel Pentium Dual-Core E5200 2.50 GHz
Disk: 500GB 7200 RPM SATA
Graphics: onboard Intel GMA 4500 chipset

---

### Post by spartan7 on 2010-09-07
I'm having the same issue using the 20' screen as an extended screen from my laptop dv2000

---

### Post by realzippy on 2010-09-07
> **spartan7 said:**
> I'm having the same issue using the 20' screen as an extended screen from my laptop dv2000

..which graphicscard driver ubuntuversion  ?

---

### Post by Calaway21 on 2010-09-07
What you have is a driver problem for your video card.

According to this [thread]("http://http://ubuntuforums.org/showthread.php?t=1398377"), Ubuntu Lucid Lynx supports this out of the box. So, if you're not running Lucid, I suggest that you upgrade your distro.

Otherwise, the first thing to do is System > Administration > Hardware Drivers. Let it look for any drivers that may be available.

If you don't find any, you can also attempt to edit the xorg.conf file and configure your display manually. To do that, go here: 

[http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")



If you screw up, go here: 

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html]("http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html")

---

### Post by realzippy on 2010-09-08
> **Calaway21 said:**
> What you have is a driver problem for your video card.

According to this [thread]("http://http://ubuntuforums.org/showthread.php?t=1398377"), Ubuntu Lucid Lynx supports this out of the box. So, if you're not running Lucid, I suggest that you upgrade your distro.

Otherwise, the first thing to do is System > Administration > Hardware Drivers. Let it look for any drivers that may be available.

If you don't find any, you can also attempt to edit the xorg.conf file and configure your display manually. To do that, go here: 

[http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")



If you screw up, go here: 

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html]("http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html")

Seems as you answered OP....this is over 1 year ago...

---

### Post by Calaway21 on 2010-09-08
> Seems as you answered OP....this is over 1 year ago...

Wow! it is. I don't really look at the dates. I just saw it at the top of the list.

---

