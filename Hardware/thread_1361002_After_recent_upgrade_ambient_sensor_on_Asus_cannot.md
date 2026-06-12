---
title: "After recent upgrade ambient sensor on Asus cannot be turned off"
date: 2009-12-21
forum: Hardware
---

### Post by Louigi Verona on 2009-12-21
Hey guys!
I am here again with the infamous (and probably unfixable) ambient sensor on asus laptops bug.
After a recent upgrade (probably, I am not sure if this is the reason) my Ubuntu Karmic presented two surprises to me:

1. Had netbook launcher on my desktop and could not be removed so I had to uninstall it.
2. Ambient sensor, which I spend so much time turning off with scripts and workarounds, mentioned here on forums, again was enabled.

I mentioned netbook launcher simply because it might help someone to debug the problem.

Redoing the known workarounds this time does not help. Although the /etc/sysfs.conf file is edited correctly and I checked the path to the file (devices/platform/asus_laptop/ls_switch=0), the ambient sensor is still enabled after reboot. Once more Ubuntu is barely usable.

It might also be useful to note that although I am absolutely positive that I inserted such a path right after upgrade to Karmic, after my recent problematic reboot the path was changed to devices/platform/**asus-laptop**/ls_switch=0

Note that in Ubuntu 9.04 it was asus-laptop, in Karmic it is asus_laptop, which caused quite some time to figure out, so I remember very well that I inserted it correctly. Somehow now it seemed to be written in an old manner, I dunno why.

Would welcome any help, I really need laptop for work and atm it is barely usable. Only to listen music, really )

---

### Post by Louigi Verona on 2009-12-21
Actually, I might add that after the upgrade touchpad stopped responding. Before it did not work correctly as well, since triggering it was by pressing a screen button, but now it also stopped working. What was in that upgrade I wonder?

---

### Post by Louigi Verona on 2009-12-22
Okay, so my battle with the light sensor continues.

For some reason the sysf.conf where the magical "devices/platform/asus_laptop/ls_switch=0" entry is, is now ignored by the system.

I have spent hours yesterday, searching the web, but I seem to be the only one affected by this.

In this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222171) a person suggested a script:

```
ian@dash:~$ cat > /etc/modprobe.d/asus-backlight-workaround.conf
# Got this from Ubuntu [bug 222171]("https://bugs.launchpad.net/bugs/222171").
install asus_laptop /sbin/modprobe --ignore-install asus_laptop; sleep 2; echo 10 > /sys/devices/platform/asus_laptop/ls_level; echo 0 > /sys/devices/
platform/asus_laptop/ls_switch;

```

It seemed to work and I was happy, but on next reboot this morning it stopped working again, ignoring this script.


Guys, can anyone please help me or at least tell me where to report all this? What is going on with my system?

---

### Post by Louigi Verona on 2009-12-22
Maybe a more general approach would help - what can make the system ignore sysf.conf? Or a modprobe.d script?

---

### Post by Nailox on 2009-12-23
KARMIC user

A) Open Terminal (Menu->Accessories), and type the following:
 	Code:
 	sudo gedit brightness 
B) Now paste the following in the Terminal window:
 	Code:
 	#!/bin/sh
echo -n 0 > /sys/devices/platform/asus_laptop/ls_switch 
C) Save your file. 

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
 	Code:
 	sudo mv brightness /etc/init.d
sudo chmod 755 /etc/init.d/brightness
sudo update-rc.d brightness defaults 90 
E) Reboot, and you will have regained control of your brightness level.

thanks to ricaxe

---

### Post by Louigi Verona on 2009-12-23
Hey!
Thanks for trying to help, but as I said earlier, I did use this kind of scripts but it did not work.

But I did manage to solve the problem!

And what did happen was that the recent upgrade of **upstart** broke smth in the system and all those init scripts were just ignored, as I thought. But downgrading to the previous version of upstart, I was able to restore the system back to normal.

---

