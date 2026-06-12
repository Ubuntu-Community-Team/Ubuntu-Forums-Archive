---
title: "Intrepid: speedstep-centrino patch for kernel 2.6.27"
date: 2008-11-04
forum: Hardware
---

### Post by nixgmx on 2008-11-04
After one night of trying to fix the broken DSDT/SSDT tables of my AMILO M 1420 (Pentium M 725 (Dothan) 1.6 GHz) I've finally given up on this task ](*,). Without proper DSDT, acpi-cpufreq won't work properly, so I am forced to continue using the "speedstep-centrino" module...

However, I have now adopted an old version (0.2.10) of the linux-phc patch ([https://www.dedigentoo.org/trac/linux-phc/](https://www.dedigentoo.org/trac/linux-phc/)) for speedstep-centrino to work with kernel version 2.6.27 :). I'm posting it here for the case that someone might need it too. PLEASE USE AT YOUR OWN RISK! This was just a quick and dirty adoption and i have only tested it on my laptop right now. But I'm hoping that it might help anyone.

---

