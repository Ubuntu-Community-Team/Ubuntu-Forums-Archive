---
title: "jaunty upgrade causes 800X600 resolution"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by gkiteguy on 2009-08-18
I am barely Ubuntu literate. I selected the package upgrade to Juanty and have been having display problems ever since 800X600. I have a Nvidia geforce2 integrated video. Ubuntu has never been happy with this but at least I got the display resolution to 1680 X 1050 before the upgrade. Now I have tried  Envy, the Nvidia site and editing the xorg.conf.  Does anyone have any ideas  I really don't need the desktop effects, but this computer has a lot of data and programs in the XP partition, or I would just try burning a CD and doing a clean install.

---

### Post by running_rabbit07 on 2009-08-18
Got to System>Administration>Hardware Drivers and install a new driver for nvidia. Let us know how that works.

---

### Post by gkiteguy on 2009-08-20
> **running_rabbit07 said:**
> Got to System>Administration>Hardware Drivers and install a new driver for nvidia. Let us know how that works.

I don't seem to have that menu item. One of the other posts I had read had me attempt to clean all the NVIDIA packages from the system. 
Maybe that caused it.

---

### Post by running_rabbit07 on 2009-08-20
> **gkiteguy said:**
> I don't seem to have that menu item. One of the other posts I had read had me attempt to clean all the NVIDIA packages from the system. 
Maybe that caused it.

Yeah, that is definitely not a good idea. Go to System>AdministrationSynaptic Package Manager and search for "nvidia" and install the one I have highlighted in my screenshot.

If you go to System>Preferences>Main Menu you should be able to added the highlighted button to your Administration Menu.

These screenshots were taken from my Virtual Box running Jaunty for best results.

---

