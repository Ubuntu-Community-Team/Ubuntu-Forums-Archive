---
title: "Uninstalling Compiz-Fusion then reinstalling it in Hardy"
date: 2008-09-02
forum: General Help
---

### Post by LeShin on 2008-09-02
Hey guys,

I while ago, I went searching for a way to install the cube reflection plugin in my default compiz fusion installation on Hardy, however i ran into some problems. I lost the control buttons in my windows bar and lost other effect functions like being able to map different wallpapers to different sides of the cube, wobbly windows and transition effects.

So I was wondering if their was a piece of code that would enable me to uninstall and then reinstall Compiz Fusion on Ubuntu 8.04 as I tried Synaptic Manager and it didn't remove everything.

Thanks in advance!

---

### Post by john.nicholls on 2008-09-03
> **LeShin said:**
> Hey guys,

I while ago, I went searching for a way to install the cube reflection plugin in my default compiz fusion installation on Hardy, however i ran into some problems. I lost the control buttons in my windows bar and lost other effect functions like being able to map different wallpapers to different sides of the cube, wobbly windows and transition effects.

So I was wondering if their was a piece of code that would enable me to uninstall and then reinstall Compiz Fusion on Ubuntu 8.04 as I tried Synaptic Manager and it didn't remove everything.

Thanks in advance!

In Synaptic, mark everything you have installed starting with Compiz and select Mark for Complete Removal to get rid of the configuration files and the program files.

---

### Post by LeShin on 2008-09-03
yeah, I did that but I still seem to have the ccsm icon in my "preferences" drop down list, though it doesn't seem to link to anything as when you click it, nothing happens. Anyway to get rid of it?

---

### Post by Shakaboom on 2008-09-03
I would like to know how to make a real fresh install too. I tried the complete removal option from synaptic, but it didn't delete everything. Some of the  configuration was the same when I installed again, not all default.

The problems are that 1) no windowmanager loads during startup, I have to reload compiz manually every boot. 2) My zoom function doesn't behave as it should. I cant click on anything anymore when zoomed in, the increments aren't right and I can't move the mouse to view other parts of the screen when zoomed in.

I get the following output when i enter in console "compiz --replace":

matthijs@matthijs-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (scalefilter) - Warn: No compatible text plugin found.

If someone could show me either how to completely start over with Compiz or fix the problems, it would be very much appreciated!

---

