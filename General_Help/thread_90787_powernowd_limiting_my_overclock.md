---
title: "powernowd limiting my overclock"
date: 2005-11-15
forum: General Help
---

### Post by Cannedbread on 2005-11-15
ive got my pentium M 1.6 overclocked to 2.13 and it runs wonderfully.

windows detects my proc as a pentium M 1.6 running at 2.13

im not sure how to check it under ubuntu but the cpu stepping applet never shows it go over 1.6, unless i uninstall powernowd, then it shows it at 2.13.

right now i have the following steps
*600mhz, 800mhz, 1gz, 1.2ghz, 1.4ghz, 1.6ghz*

i wonder if there is some way i can ad one step so it goes.
*600mhz, 800mhz, 1gz, 1.2ghz, 1.4ghz, 1.6ghz, **2.13 (Or Unthrottled)***

i tried screwing around with cpufreqd but i wasnt sure how to make it do this.

is there is a way to make the "ondemand" governor have an "unthrottled" step so it can go up to 2.13?

---

### Post by malte on 2006-05-28
I just overclocked my Athlon 64 3200+ from 2GHz to 2.4 GHz, but powernowd still keeps me at 2GHz when on heavy load!
I'm getting this old post up...

---

### Post by flapane on 2006-10-22
I have the same problem with an A64 3200+ overclocked to 2430mhz!! It only shows 1000mhz (idle) and 1800mhz (full), while they should be 1350(idle) and 2450(full).
what the hell?

---

### Post by malte on 2006-10-22
I think the only way to go is disabling Cool'n'Quiet in the BIOS or powernowd at boot if you want to overclock...

---

### Post by flapane on 2006-10-22
but I had'nt problems until 6 7 months ago (breezy badger and 2.6.9,10 and 12)

---

### Post by flapane on 2006-10-25
bump
no problem with 2.6.15, it happens with ->2.6.16 and newer

---

### Post by flapane on 2006-10-26
[http://bugzilla.kernel.org/show_bug.cgi?id=7420](http://bugzilla.kernel.org/show_bug.cgi?id=7420)

---

### Post by jhnphm on 2006-11-03
I've made a patch for 2.6.19 to fix the MHz in /proc/cpuinfo at least, but fixing it in /sys seems to be a pain (and may break powernowd/cpufreqd), so someone has to also patch the gnome applets to try /proc/cpuinfo first in conjuction w/ this patch (which is pretty crappy, but does the job of reporting correct CPU speed when cpufreq is enabled). Been having this problem w/ my overclocked core 2 duo.

---

### Post by flapane on 2006-11-04
the kde-applet first retrieves frequency from cpuinfo, then if you choose, from /sys.
Maybe you want to upload the patch in kernel mailing list, and maybe here, it will be a great work for sure

---

### Post by MakLeod on 2008-01-28
Going to /bump this thread for some more possible answers.  I have a Athlon 64 3200+ processor, and in Windows I am able to have it throttle from 1.25ghz at 1.1v to 2.5ghz at 1.42v.  In Ubuntu with powernowd, it automatically goes to back 1ghz to 2ghz.  Is there any way I can have it scale from 1.25 to 2.5ghz in Ubuntu using powernowd?  I appreciate any input anyone has on this topic.

---

### Post by Anthony M on 2008-04-07
I'm bumping this thread because it seems the problem is unresolved. 

I am also in the same situation. I have overclock my AMD 5200+ from 2.7 to 2.9 Ghz. Windows correctly reports the cpu running at 2.9 but Ubuntu (/proc/cpuinfo) still claims it is running at 2.7. 

Any suggestions are appreciated!

---

