---
title: "CPU too slow. scaling_max_frequency"
date: 2011-07-27
forum: Hardware
---

### Post by Harry Wood on 2011-07-27
My CPU has decided it's only going to run very slowly. The scaling_max_frequency seems to be set down to 800000 (800MHz) even though available frequencies are as high as 2201000 (2.2GHz)[INDENT] [FONT=Courier New]cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
800000
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
2201000 2200000 1600000 1200000 800000[/FONT]
[/INDENT]Would it be normal for the scaling_max_frequency to be equal to the highest of the available frequencies?

Can anyone tell me whether this setting is likely to be the cause of my problems? I can't work out how to change to scaling_max_freq, ...but maybe I'm barking up the wrong tree. Is it limiting me for a reason? 

I've hit this problem quite suddenly on my HP Compaq 6710b laptop, and it's completely crippled it. I've been happily running ubuntu 10.04   I didn't do anything which would have modified CPU settings, apart from maybe accepting the update manager updates.

---

### Post by TBABill on 2011-07-27
Are those settings applicable to "on ac" and "on battery" both? You have min and max frequencies, used by the CPUFREQ governor setting. The ondemand setting is default and should allow it to throttle down to your lowest setting and incrementally move up to highest based on system demand. I'm not sure if power management settings play into your frequency fluctuations while on battery power, but worth checking the system in both situations to see how it is running and compare the two.

---

### Post by Harry Wood on 2011-07-27
I installed cpufreq-info to get this read out:

[FONT=Courier New]analyzing CPU 0:
   driver: acpi-cpufrew
   CPUs which run at the same hardware frequency: 0 1
   CPUs which need to have the frequency coordinated by software: 0
   maximum transition latency: 10.0 us.
   hardware limits: 800 MHz - 2.20 GHz
   available frequency steps: 2.20 GHz. 2.20 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
   current policy: frequency should be within 800 MHz and 800 MHz.
                   The governor "ondemand" may decide which speed to use
                   within this range.
   current CPU frequency is 800MHz (asserted by call to hardware).
   cpufreq stats: 2.20 GHz:0.09%, 2.20 GHz:0.05%, 1.60 GHz:0.06%, 1.20 GHz:0.06%, 800 MHz:99.75% (182)

[/FONT](and then the same again for CPU 1)

So the ondemand governor thing seems to be active but cant do any ondemand speed choices. It's limited to 800 MHz. 

The output is the same whether I'm plugged in or not. Stuck on 800000 frequency. 

It could be something to do with power. I'm plugged in, and the screen is lighting up more and I'm not getting a battery discharging icon/warning, but maybe on some level the system thinks its not on AC Power. Any suggestions for ways of checking that? 

I've tried setting the scaling_max_freq in various ways.  
[FONT=Courier New]sudo echo 2101000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq[/FONT]
This quietly fails to change the file contents
[FONT=Courier New]sudo vi /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq[/FONT]
This reports 'E667: Fsync failed' when I try to save the chages out of vi
And finally this command fails:
[FONT=Courier New]/usr/bin/cpufreq-set -c 0 -d 2201000 -u 220100 -g ondemand
Error setting new values. Common errors:
- Do you have proper administrator rights? (super-user?)
- Is the governor you requested available and modprobed?
- Trying to set and invalid policy?
- Trying to set a specific frequency, but userspace governor is not available,
   for example because of hardware which cannot be set to a specific frequency
   of because the userspace governor isn't loaded?[/FONT]

Any other ways of changing that setting?  Is it a virtual file or what?

And one other drastic thing I tried was...  booting from a USBkey ubuntu bootdisk. This still started up (very slowly) with a sluggish 800MHz CPU too.  Does that mean this is definitely hardware problem?

---

### Post by TBABill on 2011-07-27
Generally to set cpufreq parameters you do so via ```
sudo cpufreq-set
``` and then you just add the rest of your string you tried before (-c 0 -d 2201000 -u 220100 -g ondemand)

---

### Post by Harry Wood on 2011-08-12
I don't want to speak too soon, but I think this problem is **solved**

Nothing was working to set [FONT=Courier New]scaling_max_freq [/FONT](yes as you say, I was running the cpufreq-set command with sudo) I spent a whole day trying different things but then...  I switched my laptop on the next day and it was fine!  ...for a while.

Initially this suggested overheating. Maybe a broken fan or broken heat sensor.

But there was another little hardware problem I had been noticing for several months now. My laptop power cable was a bit damaged. Occasionally the power would cut out, and I'd have to wiggle the cable to bring back power. The battery is entirely shot on this laptop, so when this happened I would know about it. But since diagnosing this CPU problem I started noticing a more subtle problem. Sometimes, even though the screen was fully lit and the charging icon was showing (the power had not cut out), the charging light on the front of my HP laptop was not lighting up. Maybe this is normal actually, but it caused me to speculate...

I've heard tell that *some laptop power cables have one or more signal wires* along with the power wire. When you first power on, the laptop fires signals down to the power brick to monitor... god knows what (can anyone confirm this? with HP laptops?) A cynical explanation would be that the evil laptop makers wanted to make it harder to get a substitute power brick, or harder to create a universal power adapter. Whatever the reason... it's apparently true of some power adapters.  So maybe my signal wires were damaged.

Solution: Buy a replacement HP power adapter!

I'm a bit surprised by this, but with a new power brick it's been happily CPU scaling for the past week (and [FONT=Courier New]scaling_max_freq [FONT=Arial]is showing as[/FONT] [/FONT][FONT=Courier New]2201000[FONT=Arial] )[/FONT]
[/FONT]

---

### Post by sbraz on 2011-08-12
> **Harry Wood said:**
> can anyone confirm this? with HP laptops?
acer aspire one 721 here: when the battery goes below a certain level a bios/acpi function forces the cpu to 800mhz, regardless of any governor setting.

some hp laptops use a special round 3 pin psu connector (19V, ground, and a "control" various voltages), others uses a round 2 pin.
i've never found a non-HP psu with a working 3 pin connector so in that case i'd recommend an original replacement.

---

### Post by chimericidol on 2011-08-12
I had EXACTLY the same problem with CPU scaling and I solved it by blowing on the CPU fan. Seems like it is dirty fans problem :)

---

### Post by doug-M on 2011-12-08
Harry Wood - good catch.

I have a Dell laptop that can take I think a 70Watt or 90 Watt power supply.
It says that it doesn't charge much or at all while running if you use the 70 Watt.

So it turns out if I use the 70watt supply my cpu freq gets stuck at 800MHz
cpufreq-info
hardware limits: 800 MHz - 2.80 GHz
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.

If I pull out the power supply and run on battery then I get:
  current policy: frequency should be within 800 MHz and 2.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.

If I plug in the 90Watt power supply I get:
  current policy: frequency should be within 800 MHz and 2.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.


So when the laptop is running with a low power power supply some interaction with ACPI ends up throttling it at 800MHz.

---

