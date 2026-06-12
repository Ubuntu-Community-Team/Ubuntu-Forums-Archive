---
title: "Trackpoint settings???"
date: 2008-12-04
forum: Hardware
---

### Post by mariner09 on 2008-12-04
I find I like my trackpoint to require a very light touch.  For me this means a high sensitivity and high speed.  I saw earlier posts that led to thinkwiki's page on adjusting the trackpoint, however, the settings don't stick.  Is something different on Intrepid as to how this is controlled?  I have the speed maxed out on the tool and the sensitivity all the way down.

If I look at the speed and sensitivity files I have the following values:

smcmackin@Mariner-T61:~/Desktop$ more /sys/devices/platform/i8042/serio0/subsystem/devices/serio2/speed
97

smcmackin@Mariner-T61:~/Desktop$ more /sys/devices/platform/i8042/serio0/subsystem/devices/serio2/sensitivity 
128

I set the desired values in /etc/init.d/rc.local with an echo -n statement, but they did not stick.

Did I just set them in the wrong file?

---

### Post by mariner09 on 2008-12-04
I dug a little deeper and found the configure-trackpoint utility on sourceforge and it's doing what I need.

---

### Post by weidongche on 2009-05-12
My T61 is running on Jaunty Jackalope.  I downloaded configure-trackpoint, and also put ```
echo -n 206 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 208 > /sys/devices/platform/i8042/serio1/serio2/speed
``` both in /etc/rc.local and /etc/init.d/rc.local.

Now the trackpoint setting would be as I set it only if I boot my laptop on electric power.  If I boot on battery power, the setting would be set to the default value which is like 128 for sensitivity and 102 for speed.  Then if I boot again on electric power, the setting would be back to what I set it.

Any idea what's going on?  Any help would be appreciated.

---

