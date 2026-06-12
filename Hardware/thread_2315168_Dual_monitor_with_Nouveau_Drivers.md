---
title: "Dual monitor with Nouveau Drivers?"
date: 2016-02-26
forum: Hardware
---

### Post by preilly on 2016-02-26
I have a dual monitor configuration.  Works well with Nvidia drivers from the standard repos, but fails when using Nouveau.  I'd like to add a 3rd display, and the Plugable USB display adaptor I have is only compatible with Nouveau according to their documentation.

When I switch to Nouveau, the 2nd monitor is always asleep.  It does show up in the Displays section of System Settings, and is listed under xrandr, but it's always asleep.

Even with Nvidia drivers, it's asleep until lightdm loads.  Then it works fine.  I'm using a standard 14.04 x86_64 installation with Unity, and an older Nvidia controller.  I have the nouveau-firmware package also.
02:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] (rev a1)

How do I get the 2nd monitor to wake up using Nouveau?

Thanks!

---

### Post by bcschmerker on 2016-03-11
Unfortunately, the task ye describe may be impossible in Nouveau, as dual-GPU support is deprecated in X.org.  As of 11 March 2016 I am working up a major-upgraded eMachines®/Acer® EL1210-09 (Advanced Micro Devices® Athlon64® LE-1620, nVIDIA® nForce® 785 MCP) for projection duty under UbuntuGNOME® 16.02b1, and the dual-display requirement ended up best filled with an upgrade video display adapter - in my case, a MicroStar® N610GT-MD1GD3/LP (nVIDIA® GF119 GPU), which can feed one display each via DVI-I and HDMI.  (I still haven't gotten the planar nVIDIA® C77 to display kernel messages properly and will probably have to retrofit a serial port and external terminal.)

---

