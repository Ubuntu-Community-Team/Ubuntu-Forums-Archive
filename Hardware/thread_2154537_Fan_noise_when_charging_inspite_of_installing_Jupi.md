---
title: "Fan noise when charging inspite of installing Jupiter"
date: 2013-06-15
forum: Hardware
---

### Post by gautamkblr on 2013-06-15
Hi guys,

I am new to this forum as well as to Linux. (former Windows user...). Im using Ubuntu 12.10 for 64-bit.

I have a brand new Dell Inspiron 15 R laptop with hybrid graphics card, Intel® Core&#8482; i5-3317U CPU @ 1.70GHz × 4 with AMD (AMD Radeon dont know exact card name).  My trouble is that when I charge my laptop the fan is noisy.  I have installed Jupiter and set it to power savings mode.  When I remove the charger the fan noise stops. Temps when I type "sensors" in terminal are as follows:

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +54.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +54.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +50.0°C  (high = +87.0°C, crit = +105.0°C)

Also I have not installed any special drivers for my video card, it's currently using X.org driver for AMD

Is everything alright with my system?

---

### Post by 2F4U on 2013-06-15
My guess is that when the machine is connected to power, processor and graphics card are running at higher frequencies, which produces more heat. Additionally, charging the battery also produces higher temperatures, and so the fans are kicking in. This is to prevent overheating.
Now, power management of the open source ATI drivers is not as good as that of the proprietary drivers. Additionally, my understanding is that the open source drivers are not able to switch between the ATI card and the other (Intel integrated?).

---

### Post by gautamkblr on 2013-06-15
Hey thanks for the reply. Yea my guess is the same. But im concerned that this fan speed increase might damage the system in anyway. That is the reason I gave the temperature readings.

---

### Post by Uriel Correa on 2013-06-15
[COLOR=#000000]Does anybody know if this board is still in production? I'd like to find out before I go to my friendly neighborhood computer store because I'm not sure I trust the guy.
[/COLOR][TABLE="width: 576"]
[TR]
  [TD="class: xl64, width: 576"][http://www.writemypaperpal.com/]("file:///C:/Users/junaid/Desktop/junaid%20june%20task%20sheet/250%20comments.xlsx")[/TD]
[/TR]
[/TABLE]

---

