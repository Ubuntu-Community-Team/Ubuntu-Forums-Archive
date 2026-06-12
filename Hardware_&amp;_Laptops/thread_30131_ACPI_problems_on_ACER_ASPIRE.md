---
title: "ACPI problems on ACER ASPIRE"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by golant on 2005-04-27
hi,
I have an acer aspire 1694 (Pentium M 2.0GHz). I installed Ubuntu on it ,but to do so I had to use the option "Linux ACPI=OFF" on bootin from CD. 
Ubuntu has been installed quite successfully (I didn't tested it very well now i didn't had time but for example lan, microfone, ATI seems to work good) but I cannot controll ACPI, battery, CPU frequency scaling and so on. In other words Ubuntu doesn't know to be on a laptop (no powernowd, laptop-mode, laptop-detect are working!!!)

I tryed to switch ACPI on and to force (ACPI=FORCE) it but it didn't worked as well (obiously). Now I use the option ACPI=OFF APM=ON on booting.

cpufreq seems to work but not as expected. I was suposed to find a /sys/devices/system/cpu/cpu0/cpufreq/ directory but it doesn't exist and I cannot check and choose cpu frequencies (no scaling_available_frequncies or scaling_governor).

No gnome CPU control and no battery control as well work

It's probably do to my CPU that has an high frequency but the computer goes quit hot when I work on it.

Can someone help me? please!!!!!!

help ](*,)  ](*,)  ](*,)  


PS: For those who bought an ACER ASPIRE 1694 and who would like to install linux and windows like me take care of partitions. You will found a ghost partition (for recovery) then a C: (fat32) and a D: (Fat32). e-

---

