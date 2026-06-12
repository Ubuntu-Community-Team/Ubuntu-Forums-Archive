---
title: "Trying to reinstall Ubuntu - Kernel panic"
date: 2011-01-15
forum: Hardware
---

### Post by WannabeKiwi on 2011-01-15
Hi all,

I've been trying to install a new graphics card into an old desktop, the efforts of which are somewhat recorded [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10357800#post10357800"), but to no avail. I thought maybe I really messed up the install of the drivers, so since I didn't have anything on there that I cared about I decided to give it a fresh start and reinstall Ubuntu. I got to the partition screen, where it subsequently failed write the partition. Since then, I've gotten a kernel panic message every time I start the installer. This is the message:

[FONT="Courier New"]udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/block/sda/sda(822)
[  180.744516] Kernel panic - not syncing: Attempted to kill init![/FONT]

This is with the alternate install CD and after I removed the graphics card completely from the tower. All searches on this error seem to point to bad memory, but I ran a test from the install and it all passed.

My system specs can be found [[COLOR="Blue"]_here_[/COLOR]]("http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T%20Series&model=T5226"). I am trying to install Ubuntu 10.04.1 32-bit.

Am I completely hosed? Did I just trash my machine somehow?

Thanks.

---

