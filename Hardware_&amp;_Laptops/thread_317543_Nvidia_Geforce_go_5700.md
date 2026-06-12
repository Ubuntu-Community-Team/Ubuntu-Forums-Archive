---
title: "Nvidia Geforce go 5700"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by xveddievx on 2006-12-12
i have been messing around with Ubuntu on my laptop for weeks now. i love it, best linux distro ive tried so far. problem is i cant get the nvidia drivers to work with my nvidia geforce go5700, they install fine but when i restart my xorg.conf using "nvidia" instead of "nv" the screen is all pixelated. i fell this is a problem with my monitor because i have used a CRT on the video out and it displays fine. please help im stuck...](*,)

---

### Post by yeehawjared on 2006-12-12
it's probably a monitor issue.  my geforce go 6800 works great on my lappy.

---

### Post by xveddievx on 2006-12-12
i believe it is something to do with the way my xorg.conf is setup or the drivers. it does the same thing on SUSE 10.1 and back when i had fedora core 4 & 5 on it, it worked flawlessly, someone must have the same problem and or know an answer for me. please help!

---

### Post by ruggerik on 2006-12-13
> **xveddievx said:**
> i have been messing around with Ubuntu on my laptop for weeks now. i love it, best linux distro ive tried so far. problem is i cant get the nvidia drivers to work with my nvidia geforce go5700, they install fine but when i restart my xorg.conf using "nvidia" instead of "nv" the screen is all pixelated. i fell this is a problem with my monitor because i have used a CRT on the video out and it displays fine. please help im stuck...](*,)

Some suggestions

May be that the installation process driver was failed and your is a mixed  modules environment. 

1) Check if the Nvidia X Server Setting Panel (Menu System) show no data of your environment. In this case check if you have these packages (mandatory) linux-headers-$(uname -r) build-essential and xserver-xorg-dev.
2) Ctrl+Alt+F1, login as user 
3) sudo /etc/init.d/gdm (kdm) stop
4) on the directory of driver sudo sh NVIDIA-Linux.xxxx.pkg1.run
5) check if in this file /etc/default/linux-restricted-modules
   there is this line 
DISABLED_MODULES="nv"
   else add it.
6)sudo nvidia-xconfig –no-composite
7)sudo /etc/init.d/gdm (kdm) start 
    
Good Luck!!
Ruggerik

---

