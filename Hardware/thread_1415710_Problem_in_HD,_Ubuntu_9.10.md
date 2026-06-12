---
title: "Problem in HD, Ubuntu 9.10"
date: 2010-02-25
forum: Hardware
---

### Post by Ain Soph on 2010-02-25
I'm using Ubuntu 9.10, and I heve a problem with power management settings. This is agressive and actually harmful.

look:

```
fdisk -l

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador do disco: 0x0ba4d1bd

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1       59321   476495901   83  Linux
/dev/sda2           59322       60801    11888100    5  Estendida
/dev/sda5           59322       60801    11888068+  82  Linux swap / Solaris

hdparm -B 255 /dev/sda

/dev/sda:
 setting Advanced Power Management level to disabled
 APM_level    = off

smartctl -A /dev/sda | grep Load_Cycle_Count

225 Load_Cycle_Count        0x0032   080   080   000    Old_age   Always       -       211835

Waiting 2 minutes

smartctl -A /dev/sda | grep Load_Cycle_Count

Waiting 4 minutes

225 Load_Cycle_Count        0x0032   080   080   000    Old_age   Always       -       211912

```How solve the problem? I set the power management off with comand "hdpram -B 255 /dev/sda". But this not solve a problem.

Info about power management of HD in Ubuntu [http://www.theworldofstuff.com/linux/ubuntufix.html](http://www.theworldofstuff.com/linux/ubuntufix.html)

---

### Post by dabl on 2010-02-25
Those are all pretty old references. This may be more useful:

[http://ata.wiki.kernel.org/index.php/Known_issues#Drives_which_perform_frequent_head_unloads_under_Linux](http://ata.wiki.kernel.org/index.php/Known_issues#Drives_which_perform_frequent_head_unloads_under_Linux)

---

