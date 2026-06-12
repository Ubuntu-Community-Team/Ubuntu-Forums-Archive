---
title: "Fan Never On + ACPI CPU Temperature is 0 Degrees Celcius"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by TheoMurpse on 2007-06-01
My laptop is an Averatec 3200 Series. ACPI works. The fan never comes on, and the computer overheats and shuts off in about 30 minutes.

When I do lsmod, fan and thermal are loaded.

Here are some of the files in /proc/acpi/thermal_zone/THRM/:
cooling_mode:
<setting not supported>
cooling mode: passive

polling_Frequency:
<polling disabled>

state:
state:           ok

temperature:
temperature:          0 C

trip_points:
critical (S5):           110 C
passive:                 90 C: tc1=2 tc2=4 tsp=30 devices=0xda5ec310 

Right now I'm sitting with the laptop positioned directly in front of a large fan and cannot carry this fan with me everywhere. Thus, I'd really like to get my fan working.

This system is a dualboot Ubuntu and Windows XP. The fan works perfect when I boot into XP.

How can I fix this? It cannot be the BIOS or broken ACPI, because as I said, it works perfectly when I boot into Windows. I also recall it working just fine in Gentoo when I had it on my laptop, but that was 2 years ago, so I may not be remembering perfectly.

---

