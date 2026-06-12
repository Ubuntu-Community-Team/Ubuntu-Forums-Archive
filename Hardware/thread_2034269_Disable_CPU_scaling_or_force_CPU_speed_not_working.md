---
title: "Disable CPU scaling or force CPU speed not working in 12.04"
date: 2012-07-28
forum: Hardware
---

### Post by elfuego on 2012-07-28
I already noticed that many people have the same or similar issue, like [here]("http://ubuntuforums.org/showthread.php?t=1283390&highlight=Disable+CPU+scaling") but I found no decent answers so far. 

I have a reliable but very slow Asus eeepc 901. In all the previous ubuntu versions I had on this netbook locking CPU speed to maximum (1.6Ghz) worked flawlessly. After the update to 12.04, the best I can get is "performance", which as you can see from the cpu-info drops the speed to 1.3Ghz. I tried forcing the governor with 
```
# cpufreq-set -u 1.6Ghz -d 1.6Ghz
```
and it sets the speed to 1.6Ghz for a random amount of time which can vary from 3 seconds to 5 minutes and then I have to repeat the command. This speed droping issue also occurs with 100% CPU usage which is really annoying. I guess I could write a script that repeats this command every 3 sec while the computer is active to make sure it stays at maximum, or I could just destroy all governors and leave only 1.60Ghz as available speed,
 but is there a more elegant solution or at least an explanation why the speed drop occurs?

```
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).
  cpufreq stats: 1.60 GHz:60.39%, 1.33 GHz:39.61%, 1.07 GHz:0.00%, 800 MHz:0.00%  (458)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
_**  current policy: frequency should be within 1.60 GHz and 1.60 GHz.**_
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).
_**  cpufreq stats: 1.60 GHz:59.61%, 1.33 GHz:40.39%, 1.07 GHz:0.00%, 800 MHz:0.00%  (460)**_
```

---

### Post by sid0972 on 2012-07-28
maybe 12.04 supports the concept of turbo, in which case the speed is max (1.6 GHz) when there is process going on consuming CPU cycles, and drops to 1.3 when near idle??
just a thought,
try installing [GPU-G]("http://www.ubuntubuzz.com/2011/05/install-cpu-g-yet-another-cpu-z-on.html"), and see the clocks of your processor at two times
1) While compressing a file
2) when doing ABSOLUTELY nothing

from the log you have shown above, speed should be 1.6GHZ when compressing, and 1.33 or 1.07GHz or 800Mhz when idle

solution apart from your's?
no idea mate

---

### Post by elfuego on 2012-07-29
> **sid0972 said:**
> maybe 12.04 supports the concept of turbo, in which case the speed is max (1.6 GHz) when there is process going on consuming CPU cycles, and drops to 1.3 when near idle??

The problem is, as I said, the CPU speed also drops when CPU load is 100% or close to 100% (compiling/flash playing/SQL query/PHP script executing etc.) :( 

I guess I'll just remove all the governors and see if that brings something. BTW, thanks for CPU-Z, never knew it existed for linux :)

**Update:** CPU drops *only* under load. In idle, its 1.60Ghz. Now this really, really sucks.

---

### Post by Yellow Pasque on 2012-07-29
Make sure your CPU temp isn't getting too high and causing it to throttle back.

---

### Post by elfuego on 2012-07-31
> **Temüjin said:**
> Make sure your CPU temp isn't getting too high and causing it to throttle back.

Thanks for the reply. The CPU isnt overheating, we are talking about intel Atom first generation here - he is as cold as mother-in-laws heart.

The problem was solved elegantly by disabling speed step in BIOS and general tardiness of the system was solved by installing Lubuntu instead. Now the system feels as if the small atom is a pure-blooded core i7 - it feels faster then Core 2 Duo w/NVIDIA GT355 on gnome :)

Great job Lubuntu devs! [-o<

---

### Post by sid0972 on 2012-07-31
looks like lubuntu us much more optimized for low performance machines
good that you solved the problem

---

