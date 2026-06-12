---
title: "Ubuntu 22.04 Screen Brightness adjustment not working, not able to connect to Wifi"
date: 2023-04-07
forum: Hardware
---

### Post by eMshsWE on 2023-04-07
I have a Dell G15 5515 Laptop Ryzen Edition. 16GB installed RAM. Processor - AMD Ryzen 5. I have dual boooted this with Ubuntu 22.04.
My laptop screen is too bright in Ubuntu. And neither are the keyboard buttons for increasing/ decreasing screen brightness working. 
Have tried installing xbacklight by using sudo install xbacklight command and testing with this :
xbacklight 30
I am getting this error message : No outputs have backlight property.
Running echo$? is giving output 1 which means previous command didn't run properly.


Also tried creating a /etc/rc.local file and edited it as follows :-
echo 150 > /sys/class/backlight/amdgpu_bl0/brightness'


When I saved and restarted Ubuntu, the brightness level hadn't reduced, same as before. Pressing hardware button does nothing. Then I checked the values by navigating to folder /sys/class/backlight/amdgpu_bl0. and tried checking brightness using vim brightness. It displays 255. and beneath shows file is read-only.


There is another folder /sys/class/backlight/nvidia


Then I rebooted in Windows 11 to check my Laptop configuration
It shows under 'Device Manager'
1) AMD Radeon(TM) Graphics
2) NVIDIA GeForce RTX 3050 Laptop GPU


I tried editing the /etc/rc.local similarly with nvidia softlink, but even that didn't work.
Also tried installing proprietary graphics drivers, NVIDIA one. After restarting in Ubuntu, my Wifi adapter is not connecting to any Wifi network.
Deselecting from the proprietary driver reverting to the open source driver and restarting does not resolve the Internet connectivity problem.


I'm forced to go to detailed GRUB options while restarting laptop, and choose a lower kernel version. Current kernel version is 5.19.0-35-generic. In detailed options, when I select kernel version 5.19.0-32-generic Wifi connectivity is restored. But the laptop brightness problem is still unresolved as before.

Could anyone help me out?

---

### Post by lucio-a on 2023-04-09
Kernel 5.19 is pretty old and your notebook model is newish, maybe you gonna have more luck with Ubuntu's newest version, 23.04.

You have 2 GPUs and the NVIDIA one is supposed to kick in if you need more graphical processing power(Games, video editing), not sure but I think Ubuntu ships with one default solution for it. You may want to look for Hybrid Graphics, this [link]("https://wiki.archlinux.org/title/hybrid_graphics") is very informative but AFAIK Hybrid Graphics were always a pain. Anyways you should give a try at 23.04 beta.

---

### Post by him610 on 2023-04-11
> My laptop screen is too bright in Ubuntu. 
One of my machines always starts up with way too much brightness. Whenever I start it up I open a terminal and enter, *xgamma -gamma 0.8* on the command line.
It lessens the overall brightness by 20% (I assume)

---

### Post by eMshsWE on 2023-05-01
To upgrade to Ubuntu 23.04, it should be possible to directly do it from terminal right (like sudo upgrade) ? Or do I have to create a bootable USB and make it install over existing partitions? And what about the 2 Kernel versions in current Ubuntu 22.04? Will they be removed and will Internet connectivity be restored when I try Ubuntu 23.04 with the higher Kernel version?

---

