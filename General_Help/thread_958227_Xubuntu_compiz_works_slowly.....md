---
title: "Xubuntu compiz works slowly...."
date: 2008-10-25
forum: General Help
---

### Post by Anharath on 2008-10-25
Hi,

I just started using Xubuntu (had Kubuntu before but I liked GNOME desktop more) and I installed Compiz succesfully. However, I'm having some problems namely: Compiz is running very slowly.. Example: the wobbly windows, the fading windows and many other effects work very slow. The only effect that's not working slowly is the 3D Cube.
I'll give you my PC Specs which i obtained useing windows before (perhaps it could be that?):
> 
OS: 			Xubuntu Hardy 8.04

Motherboard: 		Intel Easton 2 D815EEA2

Memory: 		512mB RAM
Memoryslots		
DRAM Slot #1		256 MB (SDRAM)
DRAM Slot #2		256 MB (SDRAM)

Chipset			Intel Solano i815E
On-board		
Graphical card		Intel i752

Graphical Card		ATI Radeon 9000 series 64MB

Can anyone help me out of this problem?
Thanks!

---

### Post by ajgreeny on 2008-10-25
Which graphics card is actually running and giving you the trouble?  Some ati cards are a problem with linux, but generally intel on-board cards are OK

---

### Post by Anharath on 2008-10-25
The ATI card is running it. I've installed the official ATI driver, but I haven't installed fglrx.. And I installed XGL instead of AIXGL, does that matter?
Ohyea, my CPU isn't that very up to date anymore...
Intel Pentium III CuMine (1Ghz)

---

### Post by ajgreeny on 2008-10-25
OK, I suspect that the ati card is the problem.  I think you would be better to use the open source ati driver with that card, so try using ```
gksudo displayconfig-gtk
```in a terminal and change the driver to that for a try out.

---

### Post by Anharath on 2008-10-28
> **ajgreeny said:**
> OK, I suspect that the ati card is the problem.  I think you would be better to use the open source ati driver with that card, so try using ```
gksudo displayconfig-gtk
```in a terminal and change the driver to that for a try out.
Ok, and how do I change the driver to it?
I just started using Linux so I don't quite know that much of it yet :)
Thanks!

---

### Post by hijrakom on 2008-11-27
just try to install envy it will help you to set up the driver you need:
sudo apt-get install envyng-qt .

---

### Post by Izek on 2008-11-27
Remember to first uninstall the ati driver with envy or manually before getting a driver with envy. Also, envyng-qt won't work without QT. Just install the core envyng instead, then run envyng -t (I believe) in the terminal.

---

