---
title: "A Command for Ricoh Card Readers"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by canceLinux on 2007-11-28
hi, i've edit a command for ricoh card readers (R5C*** Series, have some problems with kernel) in laptops. it finds the pci number of firewire device and resets it..

i've found this command in launchpad & edit to use with all pci numbers..

this will be publish next month in [www.enixma.org](www.enixma.org) Turkish linux e-magazine :)

```

#!/bin/bash
modprobe -r sdhci
setpci -s `lspci | grep "IEEE" | awk '{print $1}'` 0xCA=0x57
setpci -s `lspci | grep "IEEE" | awk '{print $1}'` 0xCB=0x02
# setpci -s `lspci | grep "IEEE" | awk '{print $1}'` 0xCA=0x00
modprobe sdhci
printf "%s\n" ----------- Tamamland&#305; -----------

```

(original command has 3rd line, but i run my ricoh first two command.. try it :) )

---

