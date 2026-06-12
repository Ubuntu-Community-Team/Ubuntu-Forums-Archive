---
title: "fan/cpu control"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by mättu on 2006-02-18
Dear fellow enjoyers

I'm using an Compaq Evo N800v laptop dual-booted winxp/ubuntu.
The setup was easy:
-xinxp first
-repartition HD with live-cd
-linux on 2nd partition, grub to MBR
works! cool!

Now i'm wondering if there is a possibility to fine-tune the fan settings.
I know there are several threads about this, but I have very exact questions:

Mi fans "normaly" is louder in linux than "normally" in winxp. So i monitored the temperature:
cat /proc/acpi/thermal_zone/TZ1/temperature
over 53 degree celsius the fan goes on quite loud
unter 41 degree it becomes very quiet.

Is there a possibility to set higher temperature limits? 
Especially for turning the fan almost off. Could this be set to 45 degree celsius e.g.? How?


In the meantime i surveyed the cpu-speed. Most of the time it stays at 1.2GHz and goes to max. (2.0GHz) only for short periods of high load.
I tried to throttle it down to say 600MHz. I could not. I found a setting which says that for my computer it is not possible to set it below 1.2GHz.
Can this be true?
I can't damage my computer by "underclocking" the cpu, can i?
How could one possibly set the lower limit down to whatever one pleases?

/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
perhaps?

Help much appreciated
greets
:m)

---

### Post by welsh_spud on 2006-02-18
This may/may not be of much help, but if you
```
sudo apt-get install acpi
```

Then type in ***acpi -V*** in terminal, you can get some info about the CPU temp.

*EDIT*

I've done some research and have you tried this to underclock your CPU:

echo -n **[COLOR="Navy"]NUMBER[/COLOR]** > /proc/acpi/processor/CPU0/throttling

Where **[COLOR="Navy"]NUMBER[/COLOR]**is from 0 (100% CPU) to 7 (12% CPU)

I tried it on my laptop and everything goes OK, but YMMV.

---

### Post by lzfy on 2006-02-18
I really would like to know this too. In Windows I installed a little tool :-k SpeedswitxhXP which helps me to keep the speed at 700 MHz (default is 1800). Is there a similar tool for Ubuntu? I have an Turion processor.

---

### Post by moephan on 2006-02-18
There is GNOME applet called CPU Frequency Monitor. Search these forums for how to enable the CPU speed switchig. I use this all the time.

Cheers, Rick

---

