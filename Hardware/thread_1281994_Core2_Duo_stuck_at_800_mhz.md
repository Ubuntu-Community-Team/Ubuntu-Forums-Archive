---
title: "Core2 Duo stuck at 800 mhz"
date: 2009-10-03
forum: Hardware
---

### Post by sanity on 2009-10-03
It's not entirely predictable, though it may have something to do with actual use -- that is, maybe the kernel and/or the hardware is deciding that I'm running too hot and forceably underclocking me...

Here's what I currently see, when things are working:

```
> cpufreq-info                                                   
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006                  
Report errors and bugs to cpufreq@lists.linux.org.uk, please.                   
analyzing CPU 0:                                                                
  driver: acpi-cpufreq                                                          
  CPUs which need to switch frequency at the same time: 0                       
  hardware limits: 800 MHz - 2.50 GHz                                           
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz                                                                          
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance                                                                        
  current policy: frequency should be within 800 MHz and 2.50 GHz.              
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.50 GHz:7.07%, 2.50 GHz:1.09%, 2.00 GHz:1.61%, 1.60 GHz:2.97%, 1.20 GHz:4.88%, 800 MHz:82.37%  (190864)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.50 GHz:7.41%, 2.50 GHz:2.22%, 2.00 GHz:2.52%, 1.60 GHz:3.20%, 1.20 GHz:3.82%, 800 MHz:80.83%  (192777)
```

The key line here is:

```
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
```

Note that the governor stays the same. When I ask this in IRC, most people immediately suggest making sure the governor is ondemand (it is), or making sure I'm plugged in (I am, but why should it matter?)

What happens is, the above changes to "frequency should be within 800 MHz and 800 MHz."

Changing this myself seems to have no effect, with:

```
sudo cpufreq-set -c 0 -u 2501Mhz
sudo cpufreq-set -c 1 -u 2501Mhz
```

Nine times out of ten, this returns success, but has absolutely no effect -- running cpufreq-info immediately afterwards shows I'm still at 800 MHz. It probably never has an effect, and I'm just seeing the system deciding that it's OK for me to run at full speed now.

I have no idea how long this has been happening, as the majority of my use doesn't require a particularly fast CPU. But when I need that power, I need that power, and it's getting frustrating.

System info: Kubuntu 9.04, Dell XPS M1530, /proc/cpuinfo reports Core2 Duo T9300 @ 2.50 GHz.

---

### Post by Ingenium on 2010-07-27
I'm having the same issue, and it's really annoying. There doesn't seem to be a fix yet... I think it's throttling it down thinking the temperature is too high, but acpi -V shows the temperature well below a dangerous level. Any idea how to disable temperature throttling?

---

### Post by sanity on 2010-07-28
I never did figure it out, other than that it's definitely temperature-related -- this thing just seems to get hotter and hotter, and putting a laptop cooling pad (with builtin fans) under it, even some extra space under that for ventilation, seems to make it less likely to happen.

I don't know enough about Windows to know for sure, yet, but I'm going to guess this is a hardware issue.

---

### Post by Nick_Jinn on 2010-07-28
Have you tested your benchmarks and compared it to what it was previously performing at?

---

### Post by P4man on 2010-07-28
Just to be clear: the ondemand governor will keep your cpu at 800 Mhz (or whatever is lowest) if there is no significant cpu load. you have to start a cpu intensive app to see if it works and clocks up to full speed on demand when its needed. You may already know that; but i thought Id mention it anyway as your stats seem to indicate its working completely as it should.

---

### Post by Nick_Jinn on 2010-07-28
> **P4man said:**
> Just to be clear: the ondemand governor will keep your cpu at 800 Mhz (or whatever is lowest) if there is no significant cpu load. you have to start a cpu intensive app to see if it works and clocks up to full speed on demand when its needed. You may already know that; but i thought Id mention it anyway as your stats seem to indicate its working completely as it should.


I was almost going to say that, but I assumed they knew what they were talking about since they knew to quote the system info and were familiar with the terminal....I guess other distros dont necessarily have that.

---

### Post by sanity on 2010-07-28
> **P4man said:**
> Just to be clear: the ondemand governor will keep your cpu at 800 Mhz (or whatever is lowest) if there is no significant cpu load. you have to start a cpu intensive app to see if it works and clocks up to full speed on demand when its needed. You may already know that; but i thought Id mention it anyway as your stats seem to indicate its working completely as it should.

Just to be clear: I'm quoting the MAXIMUM value of the current policy. I've verified this both with cpufreq-info, and scaling_max_freq from sysfs.

I'd hope no governor would go beyond scaling_max_freq, as that seems to be the entire point of scaling_max_freq. But it does cut down to 800 mhz.

So, in particular, this effect only occurs when I'm running a CPU-intensive app. Like earlier today, when I had a Java process using around 150% CPU (multiple threads on a dual-core system) -- tell me that's not "significant CPCU load".

No, I haven't benchmarked it scientifically. I'm not sure I have to -- it's pretty blatantly obvious when my system suddenly gets over three times slower when it trips that threshold. I've even (occasionally, not always) gotten messages in my log about temperature.

---

### Post by P4man on 2010-07-29
So are your temps really too high? If they are, is fan control working as it should?

---

### Post by sanity on 2010-07-29
> **P4man said:**
> So are your temps really too high? If they are, is fan control working as it should?

Yes, and I would guess it is. When this happens, it's generally whining like a jet engine.

I'm guessing it's something more like, the Dell guy who took it apart to repair it didn't bother replacing the thermal paste.

---

