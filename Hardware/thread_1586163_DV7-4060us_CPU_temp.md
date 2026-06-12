---
title: "DV7-4060us CPU temp"
date: 2010-10-01
forum: Hardware
---

### Post by Carl.Spackler on 2010-10-01
I have a HP DV7-4060us with the AMD Phenom II N830 2.1Ghz triple core. In Windows my CPU hovers around 45C but when testing it with Lucid or Maverick both amd64, the temp is around 60-65C. I have compiled the K10 module for use with sensors but I cannot control the fan speed and the exhaust temp from the fan is definitely hotter. I have blown out the heat sink area with a can of air and ensured that it is clean as well.

Does anyone know of a patch or a workaround that will help bring this temp down? Thanks.

UPDATE: Could just be the kernel version as listed in this thread. [http://ubuntuforums.org/showthread.php?t=1583066](http://ubuntuforums.org/showthread.php?t=1583066)

---

### Post by damipereira on 2010-11-25
Having the same problem with hp dv7-4065 same processor, I really don't know which part of the harware is causing this, CPU GPU or HDD
I'm using kubuntu 10.10 and the catayst driver that is installed by restricted driver wizard (any way to know version?)
fan speed (neither cpu nor gpu) is not reported by the sensors command, so I guess that's the problem, I'll try with another distro like opensuse 11.3 to see if it's an ubuntu-only problem

---

### Post by db260179 on 2010-12-19
I have the HP DV7 4131SA, the bios is slightly buggy and blocks the access to the fan control. I had to edit the dsdt and recompile the kernel with the new dsdt. Now the laptop is 43C before 55C.

THis link will help

[http://linux.aldeby.org/bios-dst.html](http://linux.aldeby.org/bios-dst.html)

> **Carl.Spackler said:**
> I have a HP DV7-4060us with the AMD Phenom II N830 2.1Ghz triple core. In Windows my CPU hovers around 45C but when testing it with Lucid or Maverick both amd64, the temp is around 60-65C. I have compiled the K10 module for use with sensors but I cannot control the fan speed and the exhaust temp from the fan is definitely hotter. I have blown out the heat sink area with a can of air and ensured that it is clean as well.

Does anyone know of a patch or a workaround that will help bring this temp down? Thanks.

UPDATE: Could just be the kernel version as listed in this thread. [http://ubuntuforums.org/showthread.php?t=1583066](http://ubuntuforums.org/showthread.php?t=1583066)

---

