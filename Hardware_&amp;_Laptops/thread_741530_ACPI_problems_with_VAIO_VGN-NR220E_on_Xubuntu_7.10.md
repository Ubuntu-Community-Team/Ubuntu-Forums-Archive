---
title: "ACPI problems with VAIO VGN-NR220E on Xubuntu 7.10 Gutsy"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by statokinetics on 2008-03-31
I bought this vaio a few days ago, and i'm pleasantly surprised with it, mostly. Vista ran slow as hell, so I installed xubuntu 7.10 gutsy. Immediately, I had a problem with the wifi, but the fix to that was pretty simple--I just downloaded new madwifi sources and installed them, and my wifi worked perfectly. But right now, I've got a problem with ACPI. I noticed that my FN keys weren't working, and I could not adjust my brightness. I followed instructions in these threads:
[http://ubuntuforums.org/showthread.php?t=88611](http://ubuntuforums.org/showthread.php?t=88611)
[http://ubuntuforums.org/showthread.php?t=309533](http://ubuntuforums.org/showthread.php?t=309533)
but to no avail. I've pinpointed the problem as having something to do with ACPI. An ```
lspci /proc/acpi/sony
``` reveals a blank directory when I have the sony_acpi module loaded, and no directory otherwise. I figure this is because from 7.10 onwards, ubuntu uses the sony_laptop INSTEAD of the sony_acpi module. I still tried it anyways, but it did not work. I also tried the modified fsfn at the end that was supposed to use the new sony_laptop kernel module, but it didn't seem to have any effect. Additionally, the ```
 /sys/class/backlight/sony 
``` directory mentioned at [http://www.linux.it/~malattia/wiki/index.php/Sony-laptop](http://www.linux.it/~malattia/wiki/index.php/Sony-laptop) does not exist. There is only an empty backlight directory.

Honestly, I just want to get power saving working on this laptop tvoltage+frequency throttling on both cores, low backlight power), and xbacklight DOES work. The fn volume keys (fn f4,f5) throw keycodes in xev, but the fn brightness keys (fn f5,f6) don't even register in xev. I had gnome-power-manager installed, and it did detect when I changed from ac power to battery power, but it didn't do anything (even though i set it to go down to 30% brightness, it stayed at the same brightness and made no effects). Any help regarding this would be greatly appreciated. Thanks.

---

### Post by statokinetics on 2008-04-01
Bump. Still don't know what to do.

---

### Post by wieman01 on 2008-04-01
Same problem here. I have posted a bug report on launchpad. Seems there is an issue with loading the "sony_laptop" module. It does not exist on my install.

_**EDIT:**_
I found some stuff here:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/147173]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/147173")

---

### Post by Quartz25 on 2008-04-26
I have been experiencing a similar problem, but mine was temporarily fixed.  Back in Gutsy, I was using xbacklight (and a collection of custom GUI scripts) to manage the backlight, and that worked fine.  However, when I upgraded to Hardy Heron, the xbacklight trick stopped working.  Does anyone know how to fix this problem?

Thanks in advance!

---

### Post by Quartz25 on 2008-04-26
Never mind, I found the culprit: [Bug #176888]("https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/176888").

The upshot of which is I needed to run:

```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

That gets xbacklight to work.  This may work for you!

---

### Post by rudyfella on 2008-04-29
i installed hardy with the latest updates on sony vgn-nr220e. However the command ;
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
``` 
doesn't work for me. the screen only goes blank for a second and it comes back on with no changes to the system. 

I hope i can find some help here.

---

### Post by Quartz25 on 2008-04-29
What that command does is set up the configuration correctly for xbacklight to work.  Once it temporarily blanks the screen, use the xbacklight command in the Terminal (you may have to use "sudo apt-get install xbacklight" in case you don't have the program) to change the brightness, as such:

```
xbacklight -set 75
```

This will set the brightness to 75% (changing 75 to 50 will change it to 50%, and so forth).

Sorry that this doesn't have the nice interface, but there are ways to work around it.  For example, if there's a brightness setting you like, you can use the following script, save it somewhere, and add it as a login process (via System > Preferences > Sessions):

```

#!/bin/bash

/usr/bin/xrandr --output LVDS --set BACKLIGHT_CONTROL native
/usr/bin/xbacklight -set 50

```

Also, I've written my own script for managing the backlight in Python (attached to the post).  It requires wxPython, and I'm not sure whether that's pre-installed on Hardy.  However, if that doesn't work for you, the Terminal route works just as well.

---

### Post by wieman01 on 2008-04-30
After an upgrade to Hardy (Kubuntu) my FN started working... Apparently they have fixed the stuff for my model.

---

### Post by rudyfella on 2008-04-30
thanks a lot. it worked. I had to install python-wxgtk2.8 to use the backlight manager.

---

