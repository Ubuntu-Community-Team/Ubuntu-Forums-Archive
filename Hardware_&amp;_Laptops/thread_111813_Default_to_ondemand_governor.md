---
title: "Default to ondemand governor"
date: 2006-01-03
forum: Hardware &amp; Laptops
---

### Post by Krashalot on 2006-01-03
I want to use the ondemand governor by default on my T42, with the option of manually switching to a more conservative profile when desired. I run the CPU Frequency Scaling Monitor panel applet and did the ```
sudo chmod +s /usr/bin/cpufreq-selector
``` thing so I can change the profile, but it keeps reverting to userspace every time I reboot. This has been asked in the forums before, but the responses generally suggest editing files I don't have (/etc/cpufreqd.conf).

So I tried installing cpufreqd from Synaptic and then it removed powernowd and ubuntu-desktop, which seems ok. I can now edit that file (cpufreqd.conf) to get ondemand going, but now the panel applet seems to be stuck and isn't showing the current speed (not a huge problem, but I'd like to know the current speed just for fun, and be able to use it to change the governor).

So, can I put powernowd on and just force the ondemand governor to be used at startup? If not, can I leave cpufreqd on and still have the gnome panel applet working properly?

---

### Post by basje on 2006-01-03
The default gouvernor is set when your kernel was compiled... Btw. when starting a cpufreq deamon like cpufreqd or powernowd, the script sets it to userspace, otherwise, those deamons wouldn't be very useful.

---

### Post by Krashalot on 2006-01-03
Thanks for the the reply. So does this mean I have to recompile the kernel to make this work? I'd really rather not do that...

I can switch to ondemand manually just by ```
echo ondemand > /sys/devices/system/cpu/cpu0/scaling_governor
``` so couldn't I just make that happen during bootup? I tried putting it in a few different startup scripts but it didn't seem to make any difference.

I'm not too clear on exactly how the whole cpufreq thing works - if ondemand runs in the kernel, why would anyone want a userspace daemon to run at all?

---

