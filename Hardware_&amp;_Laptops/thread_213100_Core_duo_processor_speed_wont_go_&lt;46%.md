---
title: "Core duo processor speed wont go &lt;46%"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by djoelsson on 2006-07-10
Hi,

I have a Toshiba satellite laptop with core duo centrino.  Using powernowd I can't get the processors to go below 46% speed.

I read the whole thread at [http://www.ubuntuforums.org/showthread.php?t=186003](http://www.ubuntuforums.org/showthread.php?t=186003).  

My output from  cat /proc/acpi/processor/CPU0/power is:
dan@toshiba:~$ cat /proc/acpi/processor/CPU0/power
active state:            C2
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[--] demotion[C1] latency[001] usage[04106835]


As you can see I don't have a C3 state, which is probably why my processors won't idle at any lower speed.  According to [http://acpi.sourceforge.net/wiki/index.php/WhyMyC3PowerStateIsNotUsed](http://acpi.sourceforge.net/wiki/index.php/WhyMyC3PowerStateIsNotUsed) I may have to turn off the usb bus to put my processor into C3 state.  I'm a noob, and I'm not sure how to turn it back on, so I didn't try it.  Can anyone tell me how to enable it again after I disable it?

Is there another solution?  I'm thinking I can get much better battery life if I can slow down my idle speed.

Any advice you can give me would be appreciated.

Thanks,
Dan

---

### Post by hnoble on 2006-07-10
Hi,
I had the same problem, aperently the powernowd with userspace governor does not work well with the core duo. You need to change to the ondemand governor and thus using kernel part for frequency scaling with the modules speedstep_centrino and freq_table that should already be loaded fixes this. To keep the change between reboots, install the sysfsutils package and add the following lines to /etc/sysfs.conf:

  
  devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
  devices/system/cpu/cpu1/cpufreq/scaling_governor=ondemand

---

### Post by djoelsson on 2006-07-10
Thanks for the reply.  I did as you suggested and according the CPU frequency monitor, both cores are now in ondemand mode.  However, they still sit at 46% the whole time.

Did this work for you?

Dan

---

### Post by djoelsson on 2006-07-12
Hi again,

When I run the ondemand speed governor when I'm not plugged in, the cpu usage does actually change from a constant 46%.  The only problem is that now it cycles between 46%, 61%, and 100%!  ](*,) 

Is this due to the USB bus constantly checking for new hardware that I've read about before?

Thanks,
Dan

---

### Post by Hellkeepa on 2006-07-13
HELLo!

I doubt it's that one, as that particular issue only prevents the CPU from ever reaching the C3 state (which you don't have).
Though it sounds more like you're affected by the bug discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

Read the entire thread, as I've just updated it with the current status.

Happy codin'!

---

### Post by djoelsson on 2006-07-13
Thanks again for the reply,

I feel kind of stupid right now.  I looked at the CPU status when I was not plugged in.  Now I have a C3 state!  It makes perfect sense why the processor would never go beyond C2 when it's plugged in, and only turn on C3 when running on battery.

It spends about 90% of the time in C3 and 10% in C2 when on battery.  This is only when I'm using ondemand instead of userspace, so thanks for that hint (in userspace it stays in C2).  It did add a significant amount of battery life.  The 10% in C2 is due to the cycling phenomenon I mentioned earlier.  I guess it's polling something at regular intervals...

I still can't get below 46% though, but at least I feel like I'm getting somewhere.   I wonder if this is just a hardware limitation.  I'll have to boot into windows (the horror) and see what happens there.

Thanks!
Dan

---

### Post by asmallerbrain on 2006-08-18
Bump.  I'm running edgy on a T2500 and can't throttle below ~50%.

```
~$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: centrino
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 996 MHz - 1.99 GHz
  available frequency steps: 1.99 GHz, 1.99 GHz, 1.99 GHz, 1.99 GHz, 1.99 GHz, 1.99 GHz, 1.99 GHz, 1.66 GHz, 1.33 GHz, 996 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 996 MHz and 1.99 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 996 MHz.
analyzing CPU 1:
  driver: centrino
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 996 MHz - 1.99 GHz
  available frequency steps: 1.99 GHz, 1.99 GHz, 1.99 GHz, 1.99 GHz, 1.99 GHz, 1.99 GHz, 1.99 GHz, 1.66 GHz, 1.33 GHz, 996 MHz
  available cpufreq governors: userspace, powersave, ondemand,  conservative, performance
  current policy: frequency should be within 996 MHz and 1.99 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 996 MHz.
```

The resulting frequency is the same whether I use the userspace, conservative, or ondemand governor, and whether or not the notebook (Asus Z62f) is plugged in.

It seems a bit silly that it reports 10 steps but only uses 4 different frequencies.  What on earth is going on here?

---

