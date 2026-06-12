---
title: "Compiz setup error Xgl not present on laptop ati graphics card"
date: 2008-09-10
forum: General Help
---

### Post by shadowthi3f on 2008-09-10
I recently switched to Ubuntu from xUbuntu due to buildup of incorrect setup problems (mostly mine). I was attempting to setup Compiz through the appearance menu but a error was returned while attempting to enable normal effects NOT extra effects. 
I issued the following command with this result
```
:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 


```
the last blank line is where the terminal sat for several minutes without exiting the command and I ctrl-C out.

Specs:
Intel Mobile Pentium 4 M at 1.8GHz
2x 512MB SDRAM SO DIMMs
80GB Hard Drive (exact unknown)
16MB RADEON 7000 ATI Mobility chipset
(Video chipset:
    * ATI Mobility Radeon 7000
    * AGP 4X
    * 16MB DDR-SDRAM
    * 66MHz bus
)
Ultrabay CD-RW/DVD drive


Any help or past experience appreciated.

---

### Post by ripps818 on 2008-09-10
First, install and try fusion-icon. It's able to figure out the right options to get compiz started if it's able.

Second, if that doesn't work try installing the closed fgrlx drivers. System->Administration->Hardware Drivers. Or install envyng-gtk and download newer, but less reliable ones.

---

### Post by ellalan on 2008-09-10
Hi
First you have to install simple compiz configuration settings manager in synaptics,then you will get the "custom" option in visual effects.
You have to install ccsm using synaptics and try. HTH.

---

### Post by pastalavista on 2008-09-10
You should check System > Administration > Hardware Drivers and see if the proprietary ATI drivers are installed and enabled. If not, install and enable them.
```
sudo apt-get install xorg-driver-fglrx
```
make sure your third-party repositories are included in your System > Administration > Software Sources list

---

