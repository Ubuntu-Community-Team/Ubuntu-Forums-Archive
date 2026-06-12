---
title: "Can't enable desktop effects and can't increase the screen resolution?"
date: 2010-04-07
forum: Hardware
---

### Post by sahilsonu on 2010-04-07
Hey, currently i am running Nvidia Geforce 9400gt, graphic card.
I have installed Nvidia accelerated graphic card 177 as suggested by "Hardware drivers".
Now i have two problems 
1) i can't get my screen resolution higher than 1024x768 
2) can't change my apearance setting. It promp: "could not enable desktop effects".

Here is the command "compiz" output:

sahilsk@Dragonaider:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA:     Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Any help would be great.:D


I am using Lin-x 1.1: ubuntu base linux
Version: 2.24.1
Distributor: Ubuntu
Build Date: 10/24/2008

---

### Post by coffeecat on 2010-04-07
I don't know why the proprietary driver is not being activated, but I noticed this:

> **sahilsonu said:**
> I am using Lin-x 1.1: ubuntu base linux
Version: 2.24.1
Distributor: Ubuntu
Build Date: 10/24/2008

That sounds like 8.10 (Intrepid Ibex) which is reaching end-of-life at the end of this month. End-of-life means no more updates.

Questions: is this a new install and, if so, why did you choose Intrepid?

I seem to remember there were some issues around the nvidia driver with some hardware configurations, but I can't remember the details. Whatever - you would be far better off with a later version of Ubuntu, perhaps the currect stable version, 9.10 (Karmic Koala).

---

