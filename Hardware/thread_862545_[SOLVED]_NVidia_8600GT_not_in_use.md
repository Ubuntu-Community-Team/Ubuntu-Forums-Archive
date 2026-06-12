---
title: "[SOLVED] NVidia 8600GT not in use"
date: 2008-07-17
forum: Hardware
---

### Post by Kinetica on 2008-07-17
Having massive issues with hardy upgrade and NVidia 8600GT. I can generally only get low res screen, but can occasionally get high res with a certain setup- but only one using the 'nv' driver, not the nvidia driver, and hence, cannot use compiz etc. If I try to enable the proprietary drivers it reverts to low res screen and the System>Hardware Drivers dialog presents as drivers 'enabled' but 'not in use'. I have tried many other methods, ie legacy and old drivers, tried using envy, and also tried compiling my own drivers. Nothing works. Please can someone run me through where I need to go to find the correct settings files etc.

---

### Post by StormPCs on 2008-07-17
What are your system specs including RAM?

---

### Post by Kinetica on 2008-07-17
Not sure if there's a command I could use, but this is basically what I'm running
Intel Dual core E8400 3.0GHz
4Gb DDR2 Ram
NVidia GeForce 8600GT
Release 8.04, kernel 2.6.22-14-generic

---

### Post by johnnybravo666 on 2008-07-17
I have a similar system and these are the packages I have.

-linux-restricted-modules-2.6.24-16-generic
-nvidia-kernel-common
-nvidia-settings
-nvidia-glx-new

Try completely removng the nvidia-glx-new package and rebooting. Then installing it again.

---

### Post by Duranxl on 2008-07-17
I too have had bazillion problems with nvidia drivers.
Restricted wouldnt work, envy wouldn't work, sudo sh nvidia.run wouldn't work.
but now i've found a solution that works!

On non-clean install:
->Terminal: sudo apt-get remove nvidia-glx-*
->If you have installed drivers via [www.nvidia.com](www.nvidia.com), uninstall via sudo sh NVIDIA*.run --uninstall

-->Terminal: sudo apt-get install envyng-gtk
->Applications-->systemtools-->EnvyNG
->Install NVIDIA drivers.
->Reboot
->Terminal: sudo apt-get install nvidia-settings

If it doesn't work, continue:
->Terminal: sudo rm /etc/X11/xorg.conf
->Terminal: sudo nvidia-xconfig
->Reboot (or kill X?)

---

### Post by Kinetica on 2008-07-17
Thanks JohnnyBravo, Tried to copy your setup, but alas, no dice, I can still only get low res, and no use of the proprietary drivers.

---

### Post by Kinetica on 2008-07-17
Thanks also Duranxl, but your method had no effect either. Still the same old problem, except now I don't even have the option of choosing to try to 'enable' the proprietary driver, it has gone missing completely and the Administration>Hardware Drivers dialog is now totally empty. Anmy idea how to get that back?

---

### Post by Duranxl on 2008-07-17
So did envyNG install correctly?
What happens if you launch nvidia-settings?
Have you deleted the xorg.conf to be replaced with nvidia-xconfig?

---

### Post by Kinetica on 2008-07-17
Yes envyNG istalled correctly, nvidia-settings said that the system was not using the NVIDIA X driver, and I deleted the xorg.conf and used the nvidia-xconfig all of which to no avail, and with the previous mentioned results.

---

### Post by Duranxl on 2008-07-17
> **Kinetica said:**
> Yes envyNG istalled correctly, nvidia-settings said that the system was not using the NVIDIA X driver, and I deleted the xorg.conf and used the nvidia-xconfig all of which to no avail, and with the previous mentioned results.
I also deleted all the backups in X11. No xorg files at all.
I was never able to get the driver to load until i deleted the files and used xconfig to create the .conf file (check if it does)

If all fails you could use the readme.debian in /usr/share/doc/nvidia-glx-new-envy to fix "glx" and "nvidia" etc.

Else i wouldn't know:(

---

