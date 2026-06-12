---
title: "Fan constant running, Fujitsu Amilo"
date: 2009-12-05
forum: Hardware
---

### Post by embryo_ on 2009-12-05
Edit 2013-3-5:
[Here]("http://ubuntuforums.org/showthread.php?t=1543006&page=135&p=12539056&viewfull=1#post12539056") is some experience with running later releases on the 8820.

= = = = = 


My fan is constantly running on my Fujitsu Siemens Amilo D8820. Im using the laptop to show a slideshow only, but its a bit noisy to be a picture frame... Please help.

Results of acpi -t
Thermal 0: ok, 63.0 degrees C
Thermal 1: ok, 50.0 degrees C

[Laptop specs:]("http://www.dooyoo.co.uk/laptops/fujitsu-siemens-amilo-d-8820/details/")
Processor    Intel Pentium 4 2.4 GHz
Chipset Type    SiS645DX
Type            L2 Cache - Advanced Transfer Cache
Installed Size    512 KB
Installed Size    256 MB / 2 GB (max)
Technology    DDR SDRAM
Form Factor    SO DIMM 200-pin
Type            IDE
Graphics Processor / Vendor    ATI Mobility Radeon 9000 AGP 4x
Video Memory    64 MB

---

### Post by embryo_ on 2009-12-05
Anybody?

---

### Post by bot2k9 on 2009-12-05
Well frankly speaking, what we have here is a very hot CPU (all pentium 4 cpu's are hot hot hot).
My portable turns the fan up at 60 degrees, and I have a really cool cpu (Intel P7450).
You could try cleaning the fan (if you know how to open the laptop up.) If you clean it with some compressed air, remember to block the fan so that it doesn't spin up, or else you could destroy your mainboard.

Other than that, this is absolutely normal.

Copy your /proc/cpuinfo here
"cat /proc/cpuinfo"

---

### Post by embryo_ on 2009-12-06
```
fotoramme@fotoramme:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 7
cpu MHz		: 2788.783
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid
bogomips	: 5577.56
clflush size	: 64
power management:

```

The fan is free from dust, im sure the fan didnt speed up that early and that much when i was running XP. Now it spins up seconds after Ubuntu is booted.

---

### Post by embryo_ on 2009-12-06
When i started the computer, the fan was running at full speed:
Thermal 0: ok, 47.0 degrees C
Thermal 1: ok, 38.0 degrees C

Now my computer has been on for about 5 min, fan spinning a bit slower
Thermal 0: ok, 55.0 degrees C
Thermal 1: ok, 45.0 degrees C

---

### Post by embryo_ on 2009-12-08
No ideas?

---

### Post by yossell on 2009-12-08
For my own part, the programme powertop did a great job in making my own computer run cooler and boosting battery life.

[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by embryo_ on 2009-12-08
Thanks for suggestion, tried it out but without results. The laptop is only running on AC, battery is not even installed. Weird...

---

### Post by yossell on 2009-12-08
Sorry it didn't work out with powertop.

Casting around here - could it then be that the graphics card is running hotter? On many laptops, the cpu and the graphics card share a heat pipe, so if the graphics card is stressed, the cpu temps can rise too simply because they're not getting rid of the heat as quickly along a hotter heatsink. (This happens on my laptop - not making it up!) I've an nvidia card, and there was some stuff I could do to make it run cooler in Linux - I'm not sure if anything comparable exists for Ati, but you might try it out.

---

### Post by norm7446 on 2009-12-08
Know this might sound Stupid. But do you have full airflow under the laptop, as some drag cold air in from underneath the casing and extract the hot air from a side vent. If you do not have full air flow ie: blocking the inlet vent their is no cool air coming in to cool whatever the fan is cooling. If not this. Then have a look in the BIOS as there maybe a way of setting the fan to come on at a hotter temp than the 60.0 Deg showing.

---

