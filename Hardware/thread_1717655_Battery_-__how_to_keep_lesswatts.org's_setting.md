---
title: "Battery -  how to keep lesswatts.org's setting"
date: 2011-03-30
forum: Hardware
---

### Post by hearea on 2011-03-30
Hello all. Plz help me here. I've managed to change the power saving settings as recommended by leesswatts.org, but i can't figure how to keep those settings.  They keep returning to the old states.

Is there any way to make those changes permanent?

---

### Post by Grenage on 2011-03-30
These are settings you made under *preferences/power management*, or elsewhere?  I assume you used the 'make default' option.

---

### Post by hearea on 2011-03-30
Ah, not the power management, those are fine. I meant the ones changed using terminal, such as:

mount -o remount,noatime   /
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

etc
I changed them alrite, but after restarting, they're gone, like, laptop mode's off or hda saving's also off. 

Any ideas?

---

### Post by Grenage on 2011-03-30
Odd, my install's default settings appear to be what you're trying to use.  I am going to guess (and I stress *guess*) that a boot script is resetting the values.  See the following returns:

```
grep governor /etc/init.d/*
```

---

### Post by hearea on 2011-04-03
Thanks for replying man, but it's not helping though. Anyway, i tried to change the settings manually using advanced nautilus. Then i reseted to see if it works, but guess what? It's not even booting up any more! Tried grub rescue, update bootloader n such, but none works. Took a lot of time too, so i figured reinstalling the thing may be faster. Luckily i keep /home seperately so the damage isn't big.

Ubuntu is working fine now, n i ain't messing with anything that involves either grub or root no more. if i can't change sth as admin, then i'll leave it be, for safe's sake :D

---

### Post by hearea on 2011-04-10
Well, i tried again.  when i used gksu nautilus to edit the files directly, i got this error message, maybe that's why it doesn't last after restarting. I tried adding meself with 'users and groups' to root n such, but it messed up the system. Is there anyway to make the changes permanent?

---

### Post by IcarusR on 2011-04-10
You can install the 'CPU frequency scalling applett' & add it to your pannel, then you can set to ondemand or what ever you want.

---

### Post by hearea on 2011-04-12
Thanks, i did that.  But what about VM writeback time, relatime, laptop mode etc Do i have to change them each reboot?

---

### Post by PatrickVogeli on 2011-04-12
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

---

