---
title: "need help with lm-sensors please..."
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by simianMiscreant on 2005-05-14
```
brady@theReal:~$ sensors
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and done
'modprobe i2c_sensor'!
For older kernels, make sure you have done 'modprobe i2c-proc'!
```

in gentoo, i'd just make && make menuconfig in /usr/src/linux/whateverkernel but in ubuntu i'm not familiar with compiling things into the kernel. how should i resolve this? thanks in advance.

p.s. my kernel version is 2.6.10-5.

---

### Post by nad on 2005-05-14
All you should need to do is: modprobe i2c_sensor

This will install the module in your running kernel.

To make it permanent, add the module name to your /etc/modules file.

---

### Post by Azathoth_ on 2006-10-25
I have the same issue in edgy and i cannot modprobe i2c_sensor 'cos i haven't got it with the original kernel of edgy's release.

---

### Post by JayTee on 2006-11-04
I did a search of the file system on mine, I'm running Dapper and got the lm-sensors package from the repositories. I don't have an i2c-module as far as I can see. There's an i2c-sensor.h file but that's just a header file located in /usr/include/linux. I was considering downloading the newest version off the lm-sensors website and trying to compile that. I've got the current one working but it indicates a CPU temp of about 38C but if I reboot and go into BIOS and check the temp there it usually shows about 10C hotter. Fancontrol never worked for this system. I've got an Intel D845PSN motherboard with a Pentium D 940. When the BIOS is controlling the fan it never hits full speed until it reaches 70C. Makes me think Intel is trying to slow cook their chips to burn out but not until the warranty period is up. According to thier spec sheet on the Pentium D 940 it's max temp threshold value is 100C. Anyone ever hear of the boiling point of water? Sheesh, I want  to run programs, not boil an egg or make coffee.

---

### Post by lazyd2 on 2006-11-07
> **Azathoth_ said:**
> I have the same issue in edgy and i cannot modprobe i2c_sensor 'cos i haven't got it with the original kernel of edgy's release.
Same problem here as well...

---

### Post by pitkali on 2006-11-07
Shouldn't you run something like sensors-detect ? I think I had to once...

---

