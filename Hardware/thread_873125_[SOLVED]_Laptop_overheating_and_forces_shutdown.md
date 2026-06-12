---
title: "[SOLVED] Laptop overheating and forces shutdown"
date: 2008-07-28
forum: Hardware
---

### Post by johnnybeem on 2008-07-28
I have an IBM T60 laptop and just recently installed Ubuntu. When I first installed there was a problem with it going into Standby. When I pressed the Standby button the little half-moon would just blink and computer would never actually turn off.

So I found a tutorial online (unfortunately forget which one) that told me to change processor/power settings to fix this. I did and it worked. So anyway, here's the problem.

Ever since, the laptop gets *really* hot (even when I just leave it on, but haven't used it all day it is still pretty hot). And it won't go to sleep automatically when it's on batteries. Any idea how to get this all working right??

I think part of the tutorial was to add these lines to /etc/modules if that gives you some hint of what's wrong...

cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
acpi-cpufreq

---

### Post by tamoneya on 2008-07-28
are the fans working correctly.  Sometimes on the T61 ubuntu doesnt use the fans as much as it should and you can fix it through terminal with "fan control"

[http://linux.die.net/man/8/fancontrol](http://linux.die.net/man/8/fancontrol)

---

### Post by johnnybeem on 2008-07-28
I mean, the fan feels like it's not blowing *that* hard (if at all) but I don't have much to compare it to... Lemme reboot and see what it's like in Windows, it has never overheated on me in Windows.

Uh oh... what does this mean?

$ sudo pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is thinkpad

Found the following PWM controls:
   hwmon0/device/pwm1
hwmon0/device/pwm1_enable stuck to 2
Failed to set hwmon0/device/pwm1 to full speed
Something's wrong, check your fans!

---

### Post by johnnybeem on 2008-07-28
In windows now.. It's hard to tell, neither really feels like it's *blowing* but when I put my ear next to it, can hear the fan and feel heat coming out.

If I had to say, it might be blowing a little harder in Windows but I mean, it's really hard to tell..

---

### Post by SonOfOdin on 2008-07-28
Is it dusty inside the vents?  If the heatsinks are dusty then it doesnt really matter if the fans are spinning, cool air isnt getting through fast enough to take heat out of the system.

If you have messed with voltage settings, heat is going to be a bi-product.  (Think overclocking a CPU...  you need to introduce bigger and better heat control...)

When mine is dusty, I run a vacuum over the bottom.  I have an air compressor, that I use too.  My laptop has become a desktop replacement, so it gets dusty really quick.  I ebayed a fan pad - no more overheating.

I have noticed with Ubuntu that the only time my lappy's fans spin is when Im installing software...  weird maybe but it could have something to do with the hdd getting a workout.

---

### Post by tamoneya on 2008-07-28
> **johnnybeem said:**
> In windows now.. It's hard to tell, neither really feels like it's *blowing* but when I put my ear next to it, can hear the fan and feel heat coming out.

If I had to say, it might be blowing a little harder in Windows but I mean, it's really hard to tell..

a lot of people have come to similar conclusions with T60/T61.  Try to up the fan speed manually.  I did some research on your error and there was a bug report on it.  I lost it though in my sea of tabs.  Try searching for another fan controller.

---

### Post by johnnybeem on 2008-07-29
Thanks for all the replies! I took another look at the fan, and I really am starting to think that might not be the problem. Right now my system is at 63-64 degrees (Celsius) but the fans seem to be spewing out a good amount of heat. I can hear them going just like they do in Windows.

I think it might have more to do with CPU constantly chugging away. Even when I have no programs open (just System Monitor), both CPUs (it is dual core) linger at about 8-10%. When I'm sitting here typing in Firefox, both are at about 15-20%. Is that normal? One other thing to mention is the area where the hard drive is gets WAY WAY hotter than Windows ever has. It feels like it's always spinning and never turns off...

On doing some Google searches, I stumbled across the CPU settings I changed before. I remember setting up cpufreq and getting rid of.. powernowd?

CPUs are set to powersave (see below):

```
$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
```

---

### Post by johnnybeem on 2008-08-05
Has been flawless since I changed CPU governor to from on_demand powersave...

Stays steady in the low 50 degrees Celcius

Thanks guys

---

