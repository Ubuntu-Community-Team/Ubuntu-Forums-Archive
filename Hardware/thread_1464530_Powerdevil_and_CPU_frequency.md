---
title: "Powerdevil and CPU frequency"
date: 2010-04-28
forum: Hardware
---

### Post by keljaden on 2010-04-28
I have a dell inspiron 1525 that gets a wonderful 4.5 hours of battery in windows 7, but only 2.5 in Linux Mint KDE 64 bit (which is basically kubuntu with flawless 64 bit flash support).

So, when configuring the power profiles with the "battery" widget, you can also choose the cpu power profile.

I want to find the conf file or something that I can edit where I can change what conservative and dynamic profiles actually do with the CPU frequency.

My CPU supports the ability to clock itself as low as 800mghz (I will probably go one step above that though).  Using powertop and some onther apps I determined that the default "Xtreme" power save mode only clocks my 1.87 to 1.6  which is almost nothing and the only thing that is saving battery is my monitor brightness being off.

Any help on modifying these profiles to get better battery life would be greatly appreciated.

I wouldn't mind switching my DE even if they have an app (or file) where I can easily set the power profiles to clock my cpu to what I want (on the fly).

also, I am not a linux guru so if you can, please make the instructions as simple or step by step as possible.

---

### Post by mikewhatever on 2010-04-28
Why don't you post the output of the following:

cat /proc/cpuinfo

---

### Post by keljaden on 2010-04-28
okay, here's the output;

processor       : 0                    
vendor_id       : GenuineIntel         
cpu family      : 6                    
model           : 15                   
model name      : Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
stepping        : 13                                             
cpu MHz         : 800.000                                        
cache size      : 1024 KB                                        
physical id     : 0                                              
siblings        : 2                                              
core id         : 0                                              
cpu cores       : 2                                              
apicid          : 0                                              
initial apicid  : 0                                              
fpu             : yes                                            
fpu_exception   : yes                                            
cpuid level     : 10                                             
wp              : yes                                            
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm                           
bogomips        : 3724.55                                                                      
clflush size    : 64                                                                           
cache_alignment : 64                                                                           
address sizes   : 36 bits physical, 48 bits virtual                                            
power management:                                                                              

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6           
model           : 15          
model name      : Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
stepping        : 13                                             
cpu MHz         : 800.000                                        
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips        : 3723.99
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:


And there was nothing after power manager btw.

I was in normal powersave mode when I did that and its saying my CPU is at 800 mghz and brightness is all the way off.  How come I don't get the same battery life (according to powertop estimate)  that I did in windows of ~4 hrs.  I will try and actual test in linux so see how long it lasts as well.

---

### Post by mikewhatever on 2010-04-28
Indeed, the output you posted confirms that the CPU was running at 800Mhz, but there are many other aspects like wireless and hdd. Can you post the actual output of powertop.

---

### Post by inso_741 on 2010-04-28
> **keljaden said:**
> I have a dell inspiron 1525 that gets a wonderful 4.5 hours of battery in windows 7, but only 2.5 in Linux Mint KDE 64 bit (which is basically kubuntu with flawless 64 bit flash support).

So, when configuring the power profiles with the "battery" widget, you can also choose the cpu power profile.

I want to find the conf file or something that I can edit where I can change what conservative and dynamic profiles actually do with the CPU frequency.

My CPU supports the ability to clock itself as low as 800mghz (I will probably go one step above that though).  Using powertop and some onther apps I determined that the default "Xtreme" power save mode only clocks my 1.87 to 1.6  which is almost nothing and the only thing that is saving battery is my monitor brightness being off.

Any help on modifying these profiles to get better battery life would be greatly appreciated.

I wouldn't mind switching my DE even if they have an app (or file) where I can easily set the power profiles to clock my cpu to what I want (on the fly).

also, I am not a linux guru so if you can, please make the instructions as simple or step by step as possible.

You might wanna take a look at the PHC-tool....:)
and as far as I know DE has nothing to do with powersaving although using a lighter DE then kde4(i assume)
wont hurt......

---

### Post by keljaden on 2010-04-28
I don't understand how I can have wifi on in windows 7 and get 4.5 hours... and in linux get only 2.5 if the CPU rly is at 800 mghz.  it makes no sense to me. I will post the powertop results soon.

Why is there no simple guide to "properly set up cpu frequency and power management" for KDE?  I sorta have found a few for ubuntu, but that's all.

---

### Post by keljaden on 2010-04-28
Not sure what happened, but

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 4.9%)         1.87 Ghz     0.3%
polling           0.0ms ( 0.0%)         1.60 Ghz     0.2%
C1 mwait          0.0ms ( 0.0%)         1333 Mhz     0.2%
C2 mwait          0.0ms ( 0.0%)         1067 Mhz     0.0%
C3 mwait          2.4ms (95.1%)          800 Mhz    99.3%

Wakeups-from-idle per second : 393.8    interval: 3.0s
Power usage (ACPI estimate): 12.2W (3.7 hours)

Top causes for wakeups:
  49.4% (232.0)       <interrupt> : PS/2 keyboard/mouse/touchpad
  15.3% ( 71.7)       <interrupt> : extra timer interrupt
   8.1% ( 38.0)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup)
   6.3% ( 29.7)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer)
   4.2% ( 19.7)       <interrupt> : eth2


first then

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (10.1%)         1.87 Ghz     3.2%
polling           0.0ms ( 0.0%)         1.60 Ghz     0.0%
C1 mwait          0.0ms ( 0.0%)         1333 Mhz     0.0%
C2 mwait          0.0ms ( 0.0%)         1067 Mhz     1.6%
C3 mwait          2.5ms (89.9%)          800 Mhz    95.2%

Wakeups-from-idle per second : 363.1    interval: 0.3s
Power usage (ACPI estimate): 13.3W (3.4 hours)

Top causes for wakeups:
  23.2% (  inf)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer)
  17.6% (  inf)       <interrupt> : extra timer interrupt
  15.2% (  inf)       <interrupt> : PS/2 keyboard/mouse/touchpad
   9.6% (  inf)      <kernel IPI> : Rescheduling interrupts
   8.8% (  inf)       <interrupt> : i915@pci:0000:00:02.0


Which is much much much more respectable.  I am not sure what happened...but I am content.

interestingly enough, this is with normal powersave on, xtreme powersave and agressive powersave give me less battery life...

---

### Post by mikewhatever on 2010-04-29
I don't think the CPU needs configuring, it's running at 800Mhz most of the time, according to powertop. The estimated battery life is not 2.5 hours (where did you get this), but rather 3.5.
W7 and other Windows versions usually have much better drivers, graphics, wireless, etc, with power saving enabled. Having hosts of engineers from both OEMs and MS, with readily available documentation probably helps along.

---

### Post by keljaden on 2010-04-29
i got the 2.5 hours while using powertop in "Xtreme powersave" mode and the 3.7 hours in "powersave"...I was baffled myself.  Personally 3.7 hours is just right for my needs so I am content.

---

### Post by mikewhatever on 2010-04-30
You may be interested in this power/RAM consumption comparison.
[http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1)

---

### Post by keljaden on 2010-04-30
thanks, I have seen that before. It surprises me that LXDE continues to claim is "more energy efficient" which is clearly isn't. According to those results.

---

### Post by mikewhatever on 2010-04-30
Actually, lxde scored the lowest on the battery power test.
[http://www.phoronix.com/data/img/results/linux_desktop_vitals/4.png](http://www.phoronix.com/data/img/results/linux_desktop_vitals/4.png)

---

### Post by keljaden on 2010-05-01
I didn't think that little bit would make much of a difference.  I would assume the power increase is because it requires less CPU usage to perform many of the same tasks, leading less usage of the fan.  hence less energy.

Cause if it's only 5 more min of battery life, I personally wouldn't label it as "more energy efficient"

---

