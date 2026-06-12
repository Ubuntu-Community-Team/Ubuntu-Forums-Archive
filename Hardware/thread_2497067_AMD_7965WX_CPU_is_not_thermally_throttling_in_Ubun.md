---
title: "AMD 7965WX CPU is not thermally throttling in Ubuntu 23.10"
date: 2024-04-22
forum: Hardware
---

### Post by jferments on 2024-04-22
My CPU (AMD 7965WX) is not properly thermally throttling, and is exceeding the max operating temperature of 95C without throttling (it has gotten as high as 98 before I shut it off). I am running Ubuntu 23.10, and using an ASUS WRX90E-SAGE motherboard.

If I run CPU intensive processes that max out all cores (especially if my dual GPUs are running heavy loads at the same time), I can quickly exceed the maximum temp. I'm worried that my CPU is going to get damaged. 

When I look at /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors there are only "powersave" and "performance" available ("powersave" is what it is currently set to). 

Also, when I try to set to "performance" governor in /etc/init.d/cpufrequtils and reboot, it has no effect. It just stays in "powersave" mode (which I understand will not throttle).

How can I ensure that my CPU will not exceed a specified temperature threshold (ideally ~92C or less)? Is there any way to also throttle the GPUs when CPU temps are too high?

---

### Post by Doug S on 2024-04-22
Is thermald running on your computer? What do you get for:

```
systemctl status --lines=50 thermald
```

---

### Post by jferments on 2024-04-22
```

[FONT=monospace][COLOR=#54ff54]**username@ML-tower**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemctl status --lines=50 thermald[/COLOR]
[/FONT]
[FONT=monospace][COLOR=#000000]&#9675; thermald.service - Thermal Daemon Service [/COLOR]
     Loaded: loaded (/lib/systemd/system/thermald.service; [COLOR=#54ff54]**enabled**[/COLOR][COLOR=#000000]; preset: [/COLOR][COLOR=#54ff54]**enabled**[/COLOR][COLOR=#000000]) [/COLOR]
     Active: inactive (dead) since Mon 2024-04-22 14:34:09 PDT; 26min ago 
    Process: 1878 ExecStart=/usr/sbin/thermald --systemd --dbus-enable --adaptive (code=exited, status=0/SUCCESS) 
   Main PID: 1878 (code=exited, status=0/SUCCESS) 
        CPU: 11ms 

Apr 22 14:34:09 ML-tower systemd[1]: Starting thermald.service - Thermal Daemon Service... 
Apr 22 14:34:09 ML-tower thermald[1878]: [COLOR=#000000]**Unsupported cpu model or platform**[/COLOR]
Apr 22 14:34:09 ML-tower systemd[1]: thermald.service: Deactivated successfully. 
Apr 22 14:34:09 ML-tower systemd[1]: Started thermald.service - Thermal Daemon Service.
[/FONT]
```

Just to reiterate: this CPU (AMD 7965WX) is definitely compatible with my motherboard (Asus WRX90E-SAGE), so I am not using an incompatible CPU.

---

### Post by Doug S on 2024-04-23
It is a fairly new processor. I suspect you need a newer kernel. As a test, you might want to try Ubuntu 24.04, which is due to be released later this week, I think.

---

### Post by Yellow Pasque on 2024-04-23
Personally, I think you should be able to run your CPU at full load all day and night without throttling (assuming you're not overclocking). If you can't, your cooling setup is inadequate.
A newer kernel may allow better load balancing and throttling, but if it doesn't, I'd turn off turbo boost until things are sorted and you can get better cooling.

---

