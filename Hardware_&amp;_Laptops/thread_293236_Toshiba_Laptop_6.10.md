---
title: "Toshiba Laptop 6.10"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by mondaypickle on 2006-11-04
Ive installed ubuntu 6.10 on my laptop and for the most part everything is working I just have a few problems.

1. Cpu scaling - this is basically already working, but not as good as it does in debian.  The processor is a pentium4 m 2.67 ghz.  In debian i can clock it from 333mhz to 2.67 ghz, but in ubuntu it only goes to 1.6ghz and it also shows that it will clock to 65 ghz which is obviously wrong.  I think it is becuase ubuntu loads acpi_cpufreq where i was using p4_clockmod in debian, I tried to blacklist acpi_cpufreq but that does not work.

2. lm_sensors - lm_sensors wont work in ubuntu becuase my smbus adapter is missing from lspci, it shows up fine in debian i dont know why. it is device 8086:24c3 Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03).  this is an issue because i need to manually control the fan using this sensor for the temperature, the acpi lets the cpu get to 70 C before kicking on the fan so the laptop gets too hot and the acpi themal_zone doesnt update except when the fan kicks on and off.

3. touch pad scrolling - this is really minor, but after i put the laptop to sleep and wake it up, touch pad scrolling doesnt work anymore, it works fine before going to sleep though.

4. right alt key - also minor, but the right alt key doesnt work as an alt  key, xev says its ISO_Level3_Shift? the left alt key works just fine.

Thanks for any help

---

### Post by mondaypickle on 2006-11-05
I fixed the alt key thing.  Had to mess with the keyboard settings, the alt/win keys behavior to "add the standard behavior to the menu key" and disable "use right alt to choose 3rd level"

---

