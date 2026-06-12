---
title: "CPU not scaling on Dell D620 Hardy Heron with Core 2 Duo T7400"
date: 2008-06-08
forum: Hardware
---

### Post by Dynih on 2008-06-08
As the title says I have Hardy Heron installed on my Dell D620. According to the CPU Frequency monitor, the frequency never changes from 1 GHz, depsite the maximum being 2.16 Ghz. I tried manually changing it with cpufreq-selector, but that does nothing. When I right click on the applet, it permits me to change the governor mode ("conservative","performance", etc), but it will not let me select a frequency other than 1 GHz, even when I select the performance mode.

If it's related, the computer is also currently not detecting the battery (both in the BIOS and in Ubuntu) and the battery charging light flashes amber and green.

---

### Post by chewearn on 2008-06-08
> **Dynih said:**
> As the title says I have Hardy Heron installed on my Dell D620. According to the CPU Frequency monitor, the frequency never changes from 1 GHz, depsite the maximum being 2.16 Ghz. I tried manually changing it with cpufreq-selector, but that does nothing. When I right click on the applet, it permits me to change the governor mode ("conservative","performance", etc), but it will not let me select a frequency other than 1 GHz, even when I select the performance mode.

At the moment, I'm not at my laptop so I can't verify.  But I seemed to recall a BIOS setting that need to be enabled, to allow CPU scaling.  You might want to check that.


> 
If it's related, the computer is also currently not detecting the battery (both in the BIOS and in Ubuntu) and the battery charging light flashes amber and green.

Something could be wrong at hardware level, if the light is flashing amber, while you have the AC power feed.  I have only seen this when my battery is failing or the electrical contacts are not properly made.


Finally note: could be a silly thing, but if the AC power is not properly connected, the battery will be running out (thus flashing amber), and CPU freq not scaling up due to power saving.

---

### Post by Dynih on 2008-06-08
CPU Scaling is enabled in the BIOS (or "Speedstep" as it refers to it)

The power cord is firmly connected. The battery is completely dead, as the computer is completely unable to charge it ("The system cannot communicate with this battery" is how I believe it's phrased in the bios") for a couple of days (I'm not sure when that problem arose, as I've been mainly using this computer connected to a power outlet, so it possibly could have been not charging for a while and I just didn't notice the battery slowly decreasing each time I disconnected it from AC). I'm certain, however, that's a hardware problem, seeing as it shows up in the BIOS. If it helps, the flashing is amber light thrice, then green once, and repeat and it doesn't always occur. I apologize for not being more observant with regards to when these issues appeared

I don't believe the CPU not scaling is entirely a hardware problem though, as the BIOS displays the max clockspeed of the CPU correctly as 2.16 GHz.

---

### Post by chewearn on 2008-06-08
You could remove the battery and see if the CPU scaling is working.  I have observed that when there is too much loading on the AC power (for instance, if you put in a disc in the DVD drive), the CPU refuses to throttle up.  Maybe the non-functional battery could be drawing needless current.

---

### Post by cygnine on 2008-06-08
> **Dynih said:**
> According to the CPU Frequency monitor, the frequency never changes from 1 GHz, depsite the maximum being 2.16 Ghz. I tried manually changing it with cpufreq-selector, but that does nothing. When I right click on the applet, it permits me to change the governor mode ("conservative","performance", etc), but it will not let me select a frequency other than 1 GHz, even when I select the performance mode.

You say you *are* able to set a governor? Try the following: 

```
sudo cpufreq-selector -g performance
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
```

The performance governor is supposed to automatically and always set the frequency to the highest `allowed' scalable frequency. So the output of the cat command above should be 2160000, or some such number. 

If the output is not 2160000, show the output of 
```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

---

### Post by Dynih on 2008-06-21
Ok, after selecting performance as told above, the output from cpuinfo_cur_freq is "1000000", the output from scaling_driver is "acpi-cpufreq" and the output from scaling_available frequencies is "2167000 1667000 1333000 1000000"

---

