---
title: "Star Laserprinter 8III on parallel port with Ubuntu 14.04"
date: 2016-03-13
forum: Hardware
---

### Post by florian-wendelin-mayer on 2016-03-13
Following [Tteddo]("http://ubuntuforums.org/member.php?u=255919")'s [thread from 2014]("http://ubuntuforums.org/showthread.php?t=2221990"), I wanted to share my steps to get an ancient Star Laserprinter 8III parallel printer (a Canon clone) to work under Ubuntu 14.04.

System: 
```

uname -aLinux SYSTEMNAME 4.2.0-30-generic #36~14.04.1-Ubuntu SMP Fri Feb 26 18:49:23 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux 

```

I made sure that the three required kernel modules for parallel support were loaded:
```

[COLOR=#333333][FONT=Ubuntu]lsmod | grep lp[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]lsmod | grep ppdev
lsmod | grep parport_pc
[/FONT][/COLOR]
```

 Unfortunately I did not save the output of ```
dmesg | grep par
```.

```
lpinfo -v
``` did not show any parallel port.

In the end, removing libsane-hpaio did the trick, releasing the parallel port:
```
sudo apt-get remove libsane-hpaio
```

Then, from system settings > printer > Add, the LP0 printer was available to install (under uri ```
parallel:/dev/lp0
```).

---

