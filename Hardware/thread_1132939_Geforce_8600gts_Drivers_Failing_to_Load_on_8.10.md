---
title: "Geforce 8600gts Drivers Failing to Load on 8.10"
date: 2009-04-22
forum: Hardware
---

### Post by kurry on 2009-04-22
I installed ibex by live cd. When I tried to do a straight install, it would not use the gui, but just give me a terminal. I tried the "try ubuntu" option, and this put everything in low graphics mode, saying it couldn't detect video memory, and screens were detected; but none had a usable config.
Eventually I installed ubuntu, and straight away ran the updates. It also booted in low graphics mode this time, with the same errors. After I rebooted from the updates, I installed the nvidia drivers (version 180) from the hardware manager. Now when I boot, it says something along the lines of "failed to load nvidia kernel module", aborting, and then screens found but none had a usable configuration.

Hoping that you could help me on this :/

---

### Post by kurry on 2009-04-22
bump... 
:/

---

### Post by hotweiss on 2009-04-22
1)Download the drivers

2) CTRL-ALT-F1

3) sudo /etc/init.d/gdm stop

4) sudo apt-get remove Nvidia*

5) sudo sh ./Nvidiawhateverthedriveris

6) sudo /etc/init.d/gdm restart

---

