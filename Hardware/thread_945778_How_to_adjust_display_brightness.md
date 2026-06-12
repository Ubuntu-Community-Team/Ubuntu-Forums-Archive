---
title: "How to adjust display brightness?"
date: 2008-10-12
forum: Hardware
---

### Post by JD&#322;ugosz on 2008-10-12
I'm limping along as an absolute beginner with Kubuntu on my laptop.  

Top priority:  **adjust the display brightness!**  It's all the way up and blinding, quite uncomfortable to read.

It seems to know something about the display hardware, since it uses the correct native resolution and is not too slow when scrolling and dragging windows etc.

But, I was unable to install the driver for ATI Radeon HD 2600.  I downloaded the Linux drivers from AMD, and the installer ran OK.  But it didn't seem to do anything, even after rebooting, as running their Control Center tells me the driver is not installed.

Meanwhile, the "Hardware Drivers Manager" in KDE showed only one entry, that being for the video display driver, and a sub-entry for Custom Driver.  Checking that tries to download but gives an error that it would break a package or is incompatible.

--John

---

### Post by paris_alex on 2008-10-12
Try adding the Gnome Panel called "Brightness Applet". Right click on panel, select 'add to panel'.

This would give you a button similar to volume control, instead it is for controlling brightness of your notebook.

I find this really useful even though Ubuntu supports the hardware brightness button on my notebook. Why? Because the hardware brightness button does not allow small adjustments of brightness - 1 click will give almost 50% adjustment. Maybe this is just my notebook...

---

### Post by JD&#322;ugosz on 2008-10-12
I can't find "Brightness Applet" in the corresponding location in KDE.

I search adept for "bright" and it only shows three packages; brightside, smartdimmer, and spicctrl.  The smartdimmer is already installed it tells me, but it does not work: it always tells me "failed" when I run it.

--John

---

### Post by sergiom99 on 2008-10-13
click on the battery icon in the lower right corner of your screen and then you can adjust the brightness level for each energy mode (AC or battery). Thats how I do it, besides the Fn keys in my laptop!

---

### Post by wachin on 2012-11-22
I follow these instructions:

First I Install:

kgamma
kdegraphics

I gave then right clicked on the desktop, and then run order, and a search box appears, put there "Kgamma" and appears "Gamma", I gave click and a window which says: "Gamma control module KDE" and there are all options to adjust the brightness of the monitor. I served to adjust the brightness of an external monitor (I have a Dell Inspiron 1750 laptop) brand VA1931wa-LED Viewsonic model, and worked perfectly on Kubuntu 12.04. I lowered the brightness it was too much and there was as fit (what if you could do in Windows 7 with Intel GM45 Express Chipset driver Family), so I do not burn the eyes at night.

---

