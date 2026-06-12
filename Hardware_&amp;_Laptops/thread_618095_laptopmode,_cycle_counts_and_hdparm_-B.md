---
title: "laptopmode, cycle_counts and hdparm -B"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by thj01 on 2007-11-20
I have activated laptopmode and it works fine BUT

it parks and activates the HD all the time

one hack is to change following ind /etc/laptop-mode/laptop-mode.conf

CONTROLL_HD_POWERMGMT=0 to 1

but the harddrive stil shuts down a lot of times. Following has been changed to

ENABLE_LAPTOP_MODE_ON_AC=1 (fra 0)
CONTROL_NOATIME=1, (fra 0)
LM_AC_HD_IDLE_TIMEOUT_SECONDS=600, (fra 20)
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=300, (fra 20)
NOLM_HD_IDLE_TIMEOUT_SECONDS=600, (fra 7200)
CONTROL_HD_POWERMGMT=1, (fra 0)
CONTROL_CPU_FREQUENCY=1, (fra 0)
BATT_CPU_GOVERNOR=powersave, (fra ondemand)
NOLM_AC_CPU_GOVERNOR=ondemand, (fra performance)
CONTROL_NOATIME=1, (fra 0)

Question

Can i by changing some of the parameters above to change the HD's load cycles??

do i really have to shut down APM on the hardrive completely ??? (hdparm -B 255)

what is the difference between the value 1, 127 and 255 in hdparm?

---

### Post by jespdj on 2007-11-20
> **thj01 said:**
> 
do i really have to shut down APM on the hardrive completely ??? (hdparm -B 255)

what is the difference between the value 1, 127 and 255 in hdparm?
1. No, you don't and it's probably not a good idea to do so.
2. 1 = most aggressive power management, 255 = switch off power management, 127 = somewhere in between.

See: [http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by thj01 on 2007-11-20
what does hdparm with the HD APM??

is it speed/shutdown

And do you know any places where i can read specifik about that?

---

