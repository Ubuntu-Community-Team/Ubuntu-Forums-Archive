---
title: "Custom Powernowd Parameters"
date: 2005-03-10
forum: Hardware &amp; Laptops
---

### Post by acascianelli on 2005-03-10
I'm running Hoary on my notebook.  powernowd is started on boot and correctly adjusts my cpu speed during usage.  But, the default setting for powernowd is mode 0, i want it to use mode 3.  the only way ive been doing this is killing the powernowd process then restarting it manuall with 'powernowd -m 3 &', what file would i need to edit in order to have it startup like this by default at boot time.

---

### Post by GilGalad on 2005-03-10
/etc/default/powernowd is your file.

---

### Post by acascianelli on 2005-03-10
i dont have that file

---

### Post by GilGalad on 2005-03-11
Ok, then just create one. Mine reads:

$ cat /etc/default/powernowd
OPTIONS="-q -p 1500 -m 2"

---

### Post by acascianelli on 2005-03-11
[QUOTE=GilGalad]Ok, then just create one. Mine reads:

$ cat /etc/default/powernowd
OPTIONS="-q -p 1500 -m 2"[/QUOTE]

That worked, thanks alot.  They should include that file by default in Hoary even if its blank.

Here's another question, my cpu speed range is 1.8ghz - 530mhz.  Is there anyway to force it to run at the lowest speed.  I've seen screen shots with gnome running and the cpu speed applet and when you click on it it will show you all available frequencies but mine does not do this.  My cpu is a Athlon XP-M 2400+.

---

### Post by wittygame on 2005-03-11
do chmod +s /usr/bin/cpufreq-selector

then u can switch freq. but it will not be fixed, since powernows is always dynamic and changes the frequency on the fly. the only way to do it so far  is the following:

create a file, for example /usr/local/bin/lowspeed with the following command

sudo echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

then chmod +x /usr/local/bin/lowspeed

use the command:
sudo lowspeed

this will fix the cpu to minimum, allowing it to cool down and shuttingup the horribly loud fan (i have the same machine!!). 


to go back, make the file /usr/local/bin/dynspeed with the following two lines:

echo userspace > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
/etc/init.d/powernowd restart

and run it with sudo. hitler which u have, to mee its somewhat fishy... but probably because I do not understand it...


ps. what is this sinature about

---

### Post by acascianelli on 2005-03-12
[QUOTE=wittygame]do chmod +s /usr/bin/cpufreq-selector

then u can switch freq. but it will not be fixed, since powernows is always dynamic and changes the frequency on the fly. the only way to do it so far  is the following:

create a file, for example /usr/local/bin/lowspeed with the following command

sudo echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

then chmod +x /usr/local/bin/lowspeed

use the command:
sudo lowspeed

this will fix the cpu to minimum, allowing it to cool down and shuttingup the horribly loud fan (i have the same machine!!). 


to go back, make the file /usr/local/bin/dynspeed with the following two lines:

echo userspace > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
/etc/init.d/powernowd restart

and run it with sudo. hitler which u have, to mee its somewhat fishy... but probably because I do not understand it...


ps. what is this sinature about[/QUOTE]

Its just a quote I like, im not a nazi or anything.

---

