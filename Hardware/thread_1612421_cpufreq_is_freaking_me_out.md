---
title: "cpufreq is freaking me out"
date: 2010-11-03
forum: Hardware
---

### Post by Wild-Storm on 2010-11-03
Hi,
after my system got a bit overloaded (I upgraded like 4 times) I decided to reinstall ubuntu 10.10. For now, almost everything seemed to work fine (except some flaws like nautilus not displaying exe icons blabla) but now I have a bit of a situation here. I installed cpufreq and the gnome applet as well. at first, it was always set to "performance" and I saw the bar jumping up and down but when i tried to change my cpus to 3GHZ for gaming it always went back to performance (and it did lag ingame). so I did a lsmod and saw that no acpi-cpufreq was loaded. I tried to load the module but it would immediatly "unload".

```
root@root:~# modprobe acpi-cpufreq
root@root:~# lsmod | grep acpi-cpufreq
```

But after I loaded the module, my CPU speed went straight to 3GHZ and I was unable to set it back to performance / ondemand etc

I am a bit confused as everything worked fine before the reinstall (i had upgraded to 10.10!).

any suggestions?

ps: I am running a Intel Core 2 Duo 8600

---

### Post by P4man on 2010-11-03
I dont think you need to install anything. You can just add cpu frequency monitor to your panel and be able to set the governor for a core2. Perhaps installing cpufrequtils removed whatever module really was needed. Maybe check from the livecd, it works there too.

(BTW, you shouldnt have to set it to performance, ondemand governor ought to work for almost anything. The latency for speeding up the cpu  is measured in milliseconds, once you launched a game it should run at full speed and remain at full speed)

---

### Post by Wild-Storm on 2010-11-03
oh wow that was a very nice advice. it's working fine now, removing cpufreq and cpufrequtils solved the problem :) I thought I would need them to use the applet but apparently I was wrong.

thanks a lot!

---

