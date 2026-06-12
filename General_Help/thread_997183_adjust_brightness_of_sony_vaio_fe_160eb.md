---
title: "adjust brightness of sony vaio fe 160e/b"
date: 2008-11-29
forum: General Help
---

### Post by bhagya_startup on 2008-11-29
Hi guys,

I have been trying hard to get to adjust the brightness of my vaio fe 160e/b laptop. All in vain. Graphics controller in use is Intel corporation mobile gm965/gl960 integrated graphics controller. system is using ubuntu 8.10.

ok, now the list of stuffs i already tried.
1. sudo apt-get install spicctrl
   spicctrl -b <a low value>

2. tried to compile and load the module available via
   wget [http://download.berlios.de/fsfn/sony_acpi.tar.gz](http://download.berlios.de/fsfn/sony_acpi.tar.gz) 

   this is to enable the fn keys in laptop. the output module sony_acpi.ko,
   when inserted created folder sony in /proc/acpi, with the files brightness, brightness_default and power in folder sony, according to what functionality is supported by the system using this module. But in my laptop, none of these files got created. should I assume that my laptop does not support the driver for these present in that module?

Any help on this one will be greatly appreciated. Please help !:confused:

Thank you,
bhagya

---

### Post by bhagya_startup on 2008-11-30
Hi again,

Finally the brightness adjustment worked with xbacklight module.

sudo apt-get xbacklight
xbacklight -set <value>

xbacklight -help gives you all the available options.

Thanks,
Bhagya

---

