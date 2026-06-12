---
title: "CPU Fan regulator (not lm-sensors and fancontrol)"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by NeosinneR on 2007-11-02
Hi,
I was trying to regulate my CPU fan using [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) and [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737) . But when I type pwmconfig, it wrote
> Found the following PWM controls:
   hwmon0/device/pwm1
hwmon0/device/pwm1_enable stuck to 1
Failed to set pwmhwmon0/device/pwm1 to full speed
Something's wrong, check your fans!
After some (long) time, I realizes, that it won't work (but in Windows it works perfectly, using SpeedFan). Well, I want to ask, if there is another program, which can regulate CPU fan. I have ASUS P5B and AC Freezer 7 Pro (when it's on 100%, it's really noisy, but on 60% it noiseless). Thanks for any help

---

### Post by jcsjcs on 2007-11-10
I'm having the same problem (pwmconfig aborts with the exact same error). Fancontrol used to work, but now it isn't. I'm not sure if it has to do with a recent kernel update, however:

as root:

# echo "1" >pwm1_enable 
bash: echo: write error: Invalid argument
# echo "0" >pwm1_enable 
bash: echo: write error: Invalid argument
# cat pwm1_enable 
1
# cat /proc/version 
Linux version 2.6.24-rc1 (root@hatarakibachi) (gcc version 4.2.3 20071014 (prerelease) (Debian 4.2.2-3)) #1 SMP Sat Oct 27 13:28:51 JST 2007

Any hints are welcome.

JCS.

---

