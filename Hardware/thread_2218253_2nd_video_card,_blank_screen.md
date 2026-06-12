---
title: "2nd video card, blank screen?"
date: 2014-04-20
forum: Hardware
---

### Post by Jack the R on 2014-04-20
I'm using Kubuntu 12.04

Here's what's detected - 

```
  *-display               
       description: VGA compatible controller
       product: Barts XT [Radeon HD 6870]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:b0000000-bfffffff memory:fddc0000-fdddffff ioport:be00(size=256) memory:fdd00000-fdd1ffff
  *-display
       description: VGA compatible controller
       product: GT218 [GeForce 8400 GS Rev. 3]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:19 memory:fb000000-fbffffff memory:c0000000-cfffffff memory:de000000-dfffffff ioport:cf00(size=128) memory:d0000000-d007ffff

```

The Radeon is the first card and is running two monitors more or less o.k.  The Geforce is the new one, with a third monitor that is displaying a blank screen.  

I followed the instructions here to configure the Geforce - [Link](http://dragly.org/2012/05/04/installing-the-nvidia-driver-in-kubuntu-12-04/)

Systems Settings shows nothing for the third monitor.  

Help?

---

### Post by QIII on 2014-04-20
Hello!

Unfortunately, in the Linux world using GPUs from different OEMs is not likely to produce satisfactory results.

If this is for a gaming environment, you would be better choosing one or the other and using the appropriate proprietary driver.

It is possible that you might get some results from uninstalling all proprietary graphics drivers and using the default open source drivers.  But your performance might suffer in gaming or graphics intensive applications.

It may still not work with the open source drivers, but I would not bet the farm on finding any way to use both cards with proprietary drivers.

---

### Post by Jack the R on 2014-04-20
Hmm, I Googled up a few sites the other day saying it would be no problem in Linux, but I suspect you are right all the same.

So I have run sudo apt-get purge nvidia-current

I don't know if this has accomplished anything or not though.

I get an error when I try to change the window compositing from Xrender to OpenGL, and if I try to start Blender I get the error - 

```
Xlib:  extension "GLX" missing on display ":0".
intern/ghost/intern/GHOST_WindowX11.cpp:199: X11 glXQueryVersion() failed, verify working openGL system!
initial window could not find the GLX extension, exit!

```

In the short term I need to get the video drivers back to where they were so I can run Blender again.  In the long term I'll replace the Radeon with a newer nvidia card.

---

