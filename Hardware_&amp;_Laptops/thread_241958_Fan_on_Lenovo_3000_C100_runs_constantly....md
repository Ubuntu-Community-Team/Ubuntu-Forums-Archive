---
title: "Fan on Lenovo 3000 C100 runs constantly..."
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by LinLenLap on 2006-08-23
Hi, I've got Ubuntu Dapper Drake running on a Lenovo 3000 C100. It's got a Celeron M Processor at 1.5Ghz. The problem is that the fan kicks in about every 15 seconds for a good 15 to 20 seconds, regardless of whether I'm writing an email, watching a video while surfing the net, or just sitting there staring at the desktop.

I want to enable the 'ondemand' frequency governer, but I haven't been able to find simple enough explanations for me to follow. I'm a real nube. I'm writing this on wireless goodness, watching videos, etc., but that's just because so far everything has "just worked". I can't even tell you whether or not I've got any kind of govenor installed right now. The folder on the posts I read that people said to edit isn't even on my system.

Many thanks,

LinLenLap
=======================================
Linux, Lenovo, Laptop....awwww...Lucky!

---

### Post by T8y8 on 2006-08-23
I just did this a few minutes ago.

[http://martin.ankerl.org/2006/08/16/how-to-make-firefox-40-percent-faster/](http://martin.ankerl.org/2006/08/16/how-to-make-firefox-40-percent-faster/)

Is a very simple and easy-to-follow link.

---

### Post by LinLenLap on 2006-08-23
Yes, I had found that link also. What worried me though was this:

"I have a centrino, you might need a different module"

I don't have a centrino...how do I know if I need another module, and how do I discover which module I need?

Best,

LinLenLap

---

### Post by evil_elman on 2006-08-23
Do the Celeron M's alternate the frequencies at all? I've got a Pentium M and it works fine but my girlfriends laptop has got a Celeron M which (in Windows) doesn't scale the CPU frequency whatsoever.

---

### Post by LinLenLap on 2006-08-23
I've seen successful reports of people using the Ondemand governor in Gentoo.

I've had no luck using powernowd, but I think that's because the celeron's aren't able to be scaled from the userspace.

I think I said all that right.

Right now I'm looking at my cpu freq's and it just remains stuck at 1.5... so at least I know I've nailed the source of the fan problem. 

Now if someone can help me understand how to enable ondemand for a celeron m processor I would be deeply grateful.

Best wishes,

LinLenLap

---

### Post by LinLenLap on 2006-08-24
Ok, I found the following on line at this location: 

[http://www.plenz.com/thinkpad_R50e#cpufreq](http://www.plenz.com/thinkpad_R50e#cpufreq)

To quote:

"The built in Intel Celeron M 1500MHz can be throttled to seven different speed levels:

    * 187MHz
    * 375MHz
    * 562MHz
    * 750MHz
    * 937MHz
    * 1125MHz
    * 1312MHz

In order to do that you have to load the following kernel modules: p4_clockmod, cpufreq_userspace and speedstep_lib. Best is to add these modules to /etc/modules.

After that you can either set the CPU frequency manually, by echo'ing the MHz values in one of the files placed under /sys/devices/system/cpu/cpu0/cpufreq. It is however much handier to use a governor or a daemon for this. I used to use cpufreqd to do that. Now I use the kernel governor ondemand to do that job.

I have written a little script I placed under /etc/init.d/cpufreqondemand. When started the script enables the governor, loads the module if not already loaded and sets a minimum clock speed of 562MHz.

#!/bin/sh

case "$1" in
    start)
        modprobe cpufreq_ondemand
        echo 562000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
        echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
    ;;

    stop)
        echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
    ;;

    *)
        echo "Usage: /etc/init.d/cpufreqondemand start"
        exit 1
    ;;
esac"

My questions:

1. How do i load those modules?
2. Is there another way to initiate it, say, set it to something like default, rather than running his script at boot, which I don't really understand?

Best,

LinLenLap

---

### Post by LinLenLap on 2006-08-27
*Bump.

---

### Post by LinLenLap on 2006-09-03
Success.

I recompiled the kernel (any way to change CPU type and enable ondemand at boot within the kernel without rebuilding?) and changed my cpu type to celeron (Pentium compatiable), set ondemand to load in the kernel at boot. Uninstalled powernod. Changed the default governor from performance to ondemand. Scaling heaven

---

### Post by darrenm on 2007-01-31
On Edgy I just had to install cpufreqd and put the above mentioned modules in /etc/modules then reboot.

---

