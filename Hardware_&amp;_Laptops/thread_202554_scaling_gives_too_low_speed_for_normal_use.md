---
title: "scaling gives too low speed for normal use"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by Eversmann on 2006-06-23
Hello.

I've being searching for this for coulnd't find a suitable solution.

on my fujitsu laptop (with celeron 1.6) i could make scaling to work using p4_clockmod on /etc/modules and powernowd

The thing is: it has 8 steps. 200-400-600-800-1000-1200-1400-1600

On normal use, it goes down to 200Mhz, that makes the desktop sluggy, slow and uncomfortable.

Is there any way to fix it?

I tried to tweak the scaling_available_frequencies on file:///usr/share/ubuntu-artwork/home/locales/index-es_ES.html/sys/devices/system/cpu/cpu0/cpufreq but it fails on fsync saying the file is in use.

Anyone had that problem too?

Thanks a lot.

EDITED:

I solved it after looking at /etc/default. I forgot i installed cpufrequtils package.

If you into it, you'll see:

ENABLE="false"
GOVERNOR="ondemand"
MAX_SPEED=0
MIN_SPEED=0

i set it this way:

ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED=1600000
MIN_SPEED=800000

after that, i run sudo /etc/init.d/cpufrequtils restart

and now works like i wanted.

If you see the lines, enENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED=1600000
MIN_SPEED=800000

enable=true makes it to work on booting up. Governor say what is the governor you want to use (userspace, performance, etc..)
Min and Max speed says what is the minimun and maximun clock frequency you want to run the stepping.

Hope it helps.

---

### Post by ape on 2006-06-23
What happens if create the file /etc/default/powernowd containing the following line:

OPTIONS="-q -l 50"

and restart /etc/init.d/powernowd

NOTE: that is a lower case "L", not an "I"

---

### Post by Eversmann on 2006-06-23
Thanks for your reply. I solved the problem tweaking the file /etc/default/cpufrequtils like i edited on my original post.

---

