---
title: "DVD burn stations messed up in KDE / K3B"
date: 2014-05-05
forum: Hardware
---

### Post by hjvdmolen on 2014-05-05
After upgrading from Kubuntu 13.04 to 13.10 with KDE 4.11.5 and K3B 2.02, my (2) dvd burn stations are messed up in K3B / KDE.

1. When I place a data dvd in /dev/sr0, KDE automatically mounts it; 
but when I eject the disk via the notifier, it eject /dev/sr1 (the drive below!)
The same disk inserted in /dev/sr1 is not recognised by KDE; 

2. A blank dvd in /dev/sr0 is recognised by KDE, but not by K3B; 
in its setup, K3B lists /dev/sr1 as the only disk station (always empty).

3. when I do [bash] "udisk --monitor" and insert disks in both stations, it shows appropriate messages "changed:     /org/freedesktop/UDisks/devices/sr0", also for /dev/sr1

4. Looking at ~/.kde/share/config/k3brc shows noting unusual:
[Devices]
HL-DT-ST DVD-RAM GSA-H54N=8468,8468
...

I'm trying to find out is this is just a configuration issue or a hardware malfunction.
Any suggestions?

---

