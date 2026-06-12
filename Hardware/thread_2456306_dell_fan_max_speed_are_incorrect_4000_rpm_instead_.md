---
title: "dell fan max speed are incorrect 4000 rpm instead of 6200 rpm"
date: 2021-01-09
forum: Hardware
---

### Post by samuaz2 on 2021-01-09
Hi 

I'm trying to make the fans of my dell alienware m15r3 and m14xr2 Works as Windows in my ubuntu 20.04, I can successfully load the dell-smm-hwmon by 
 
Sudo modprobe dell-smm-hwmon force=1 or dell-smm-hwmon ignore_dmi=1
 
Then i able to change the fan speed using the i8kutils or manually echo over the pwm without need to use a trick to try to disable the bios control.
 
The problem that I have is that at max speed the module is only putting my fans at 4000 rpm max, but my both alienware laptop have a max fan speed of 6200 rpm (performance/turbo mode)
 
So doing:
 
i8kfan 1 0 -> 0 rpm
i8kfan 1 1 -> 2000 rpm
i8kfan 1 2 -> 4000 rpm
 
also, if I try to change it using the echo over the pwm1 for example:
 
echo  255 >> pwm1 -> 4000 rpm
 
I already try to load the module with the fan_max=3 but not luck max speed 4000 rpm.
 
Do you know what can I do to solve this and make my fans max speed be the real speed 6200 rpm?
 
Thanks

---

