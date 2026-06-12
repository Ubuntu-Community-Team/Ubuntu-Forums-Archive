---
title: "Help me plz"
date: 2008-07-17
forum: General Help
---

### Post by Forcvcr on 2008-07-17
Hello everyone, i recently installed ubuntu in my computer for the first time,so its my first time using linux, and i have a problem with desktop effects, whenevr i try to enable them it says they cant be enable, ive been searching the forums all.... day and ive tried some stuff, but i cant get it to work. im not sure how to install the graphics card drivers and it says that my graphics card does not support compiz, is there anyone that can help a first time linux user with this please? if this is any help this is what im currently running.

Ubuntu:
release 8.04(hardy)
Kernel linux 2.6.24-19-generic
Gnome 2.22.2

Processor:
AMD athlon 64 x2 6400+

Graphics card:
Chipset Manufacturer: 	 NVIDIA
GPU: 	GeForce 9600 GT



this is what it says..

> Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation Geforce 9600 GT 512mb (rev a1)
 Driver in use:         nv
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: nv driver in use 

Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y
administrator@administrator-desktop:~$ WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia failed: modinfo: could not find module nvidia

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy


---

### Post by stitchmysmile93 on 2008-07-17
Install envy and run it.. follow the directions it gives you.. once you have that installed and it's working install compiz, advanced desktop effects settings, emerald, and compiz fusion icon.. 

Once you have all that install go to system> preferences > advanced deasktop effects settings and configure your desktop.. you can use emerald to do some configuring too I use both... I even use default configuration settings too..

Have fun...

---

### Post by diafanos on 2008-07-17
What if you go:
System -> Administration -> Restricted Drivers Manager.

is there your graphics card driver?
Is it enabled?
If not, check: Enabled and let system download all necessary packets.

After that, restart Ubuntu and you'll probably have no more graphics problem.

---

### Post by Forcvcr on 2008-07-17
thanks you guys, i fixed it with your help, thx alot again, appreciate the help

---

### Post by bangeko on 2008-10-27
Note:
There will be no restricted driver list before you install linux-restricted-modules

---

### Post by tuxxy on 2008-10-27
You will need the v177 nvidia drivers for that card

---

