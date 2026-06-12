---
title: "Disable thermal shutdown? HELP - Ubuntu 10.04"
date: 2010-08-01
forum: Hardware
---

### Post by prytoluk on 2010-08-01
Hey guys, how you're doing?

I've been the whole week searching for an awnser for my problem, but i just can't. So i'm begging you some help here.

My brand new laptop was suddenly turning off with high fans activity, and i didn't knew what was happening. Throug some logs i could finally realize that it was thermal shutdowns, and the log files said the temperature was 172º C, which is enough to explode a computer. But it only happens SOMETIMES, and ONLY after 1 min of ubuntu loaded. I've readed lots of complaining about irregular sensor activity, so i want to disable this thermal shutdowns.
I've read a bunch of tutorials, but none of them explained anythiung for ubuntu 10.04. I've tried creating an "options.conf" file at "/etc/modprobe.d/" with the command line "options thermal nocrt=1", but i doesn't work.

I could manage to turn acpi=off, but it won't let my pc shutdown.
I'm  VERY frustated, so if anyone could tell me how i should proceed i'd be VERY gratefull.

Thanks!

---

### Post by ram0042 on 2010-08-01
Are your fans running? because if you disable the thermal shutdown, you might damage your system, my Toshiba Satellite shuts down only with certain apps that cause it to overheat quickly. So what i think you would want to include in a script is for your fans to run constantly and have the sensors turned off

---

### Post by prytoluk on 2010-08-01
My fans are running smoothly, but i can hear them if i get my head near the laptop. I don't think i need a script to turn my fans on, beacause they already are. My sensors seems to act normally, i get a 31ºC temperature right now, but i have this bug right after the boot, so i need to disable the thermal shutdowns, as in "options thermal nocrt=1".

Thx for the help.

EDIT: OK, i've found the solution:
In my "/etc/default/grub" file i edited the "GRUB_CMDLINE_LINUX_DEFAULT" line so it would be like "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash thermal.nocrt=1"", i did a "sudo update-grub" and voila, it works, after a reboot i did the "cat /proc/acpi/thermal_zone/*/*" comand and it showed that the critical temperature is disabled.

I didn't want to set it that way, but the instant shutdowns we're pissing me off.

---

### Post by TBABill on 2010-08-01
You stated 172C. Are you sure that wasn't 172F? My Dell laptop and both Acer laptops shut down right around 100C, but I have taken steps so they never get that hot. I use CPU frequency scaling, use only the proprietary drivers for my video cards and use only Adobe Flash and Sun Java (not open source versions). All these steps, with CPU scaling set to "ondemand" have kept my machines at 60C or lower almost all the time.

My suggestions are to try those I have done above and see if they help. If you need help with cpufreq-utilities just search CPUFREQ. To set it once installed, just type> sudo cpufreq-set --governor ondemand in a terminal. Then exit and enjoy. To verify what it is set to use > cpufreq-info in a terminal.

---

### Post by prytoluk on 2010-08-02
> **TBABill said:**
> You stated 172C. Are you sure that wasn't 172F? My Dell laptop and both Acer laptops shut down right around 100C, but I have taken steps so they never get that hot. I use CPU frequency scaling, use only the proprietary drivers for my video cards and use only Adobe Flash and Sun Java (not open source versions). All these steps, with CPU scaling set to "ondemand" have kept my machines at 60C or lower almost all the time.

My suggestions are to try those I have done above and see if they help. If you need help with cpufreq-utilities just search CPUFREQ. To set it once installed, just type in a terminal. Then exit and enjoy. To verify what it is set to use  in a terminal.

It could be a temperature in fahrenheit, but 172º F is about 78º C, and my critical temperature is 105º C (it wouldn't be fahrenheit, since it would be about 40º C). I don't have any heating problem, and my fans are ok. Before i did that "fix" i could let the laptop on for hours, with no heating problem, and the sensors pointing to 31-40ºC. The only problem i have is 1 minute after the boot, and it happens sometimes.

I have no FIX, but since there is complainments about errors on the temperature sensors, there could be no fix to it yet. 

Thx anyway!

---

