---
title: "NVidia hates my system..."
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by Darthpip on 2005-02-08
Hey all.

I recently installe the NVidia drivers for Ubuntu, and shortly after, my computer would constantly crash. It was getting pretty bad, so I did a fresh install, and I'm at the point where I'd like to install them. What I'd like to know right now is what I need. I'm following the guide from Ubuntuguide.org

Here are a couple of quick questions.

What Kernel do I need?
Any way to enable OpenGL without a driver?
Any other requirements?

Thanks in advance.

P.S. I simply love Ubuntu!! Better than FC3, and Ark Linux, very newb friendly!

---

### Post by crane on 2005-02-08
[QUOTE=Darthpip]Hey all.

I recently installe the NVidia drivers for Ubuntu, and shortly after, my computer would constantly crash. It was getting pretty bad, so I did a fresh install, and I'm at the point where I'd like to install them. What I'd like to know right now is what I need. I'm following the guide from Ubuntuguide.org

Here are a couple of quick questions.

What Kernel do I need?
Any way to enable OpenGL without a driver?
Any other requirements?

Thanks in advance.

P.S. I simply love Ubuntu!! Better than FC3, and Ark Linux, very newb friendly![/QUOTE]


I really don't think the kernel matters. I have had nvidia drivers running on both. I just used apt to install and config it.
Have you done any tweaking to you XF86Config-4 file? (refresh rate or resolutions)

Also look at the XF86Config-4 file nad make sure the lines 
load  "dri"
Load  "GLCore"
are removed or commented out.

Also look at you log files and see if you can tell what is causing the crash. Is it random?

---

### Post by Darthpip on 2005-02-08
[QUOTE=crane]I really don't think the kernel matters. I have had nvidia drivers running on both. I just used apt to install and config it.
Have you done any tweaking to you XF86Config-4 file? (refresh rate or resolutions)

Also look at the XF86Config-4 file nad make sure the lines 
load  "dri"
Load  "GLCore"
are removed or commented out.

Also look at you log files and see if you can tell what is causing the crash. Is it random?[/QUOTE]

Ah, I missed that step. I've actually had to reboot my system, and i never thought about looking at the logs.

I can tell you what happens, though. About 10-15 minutes into starting my computer, the monitor will flicker, then my computer freezes up. Occasionally the disply will soften up. It's quite odd.

---

### Post by crane on 2005-02-08
hmmm. I haven't seen this myself. 
So you don't have this problem when the driver is set to nv?

You could check that also, I forgot to mention it.

Look in you /etc/X11/XF86Config-4 file/ you should see aomething like:

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200 Ultra]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

That  driver should set to "nvidia" if you have installed the nvidia drivers and "nv" if you have not.

---

