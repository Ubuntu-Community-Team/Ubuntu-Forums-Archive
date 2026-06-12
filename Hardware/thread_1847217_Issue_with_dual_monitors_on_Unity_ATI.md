---
title: "Issue with dual monitors on Unity ATI"
date: 2011-09-20
forum: Hardware
---

### Post by Hammeh on 2011-09-20
Hey!
This is my first post so please go easy on me!

I recently moved from Fedora 15 to Ubuntu 11.04 on my Dell Studio 1555 Laptop. It has a ATI Radeon 4500 series graphics card, although I am not sure which one. Running lspci gives:
"VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500/5100 Series]"

I have an external monitor connected (to the right of my laptop), which is a wee 15 inch 4:3 HP screen. I am not running the closed source ATI driver because it gives me a whole heap of problems such as no dual screen in Unity-3d and awful screen flicker when playing Java games. 

My problem is this, when I maximize a window, primarily firefox I am using, 1 pixel from the firefox window appears on the second screen. Its not a big problem, but it can be very distracting in the corner of your eye when I am watching a movie or something.

I have no xorg.conf file configured as the screens run at full resolution without it. I have however edited ~/.config/monitors.xml to set my laptop screen as the primary monitor.

Any help on how to fix this issue would be most appreciated!
Thanks
Peter

---

### Post by Hammeh on 2011-09-21
Still having this issue after fiddling with it all day yesterday =(
Anyone got any suggestions? Do i need an xorg.conf file?

Peter

---

### Post by Lamukra on 2011-09-30
> **Hammeh said:**
> Still having this issue after fiddling with it all day yesterday =(
Anyone got any suggestions? Do i need an xorg.conf file?

Peter

For me solution was pretty easy though.
I am using Sony Bravia TV through HDMI connector and exactly same issue I had :)

I just went to setting of my TV and there was option Screen Position Correction.
Try to find something like this in your HP monitor.

Small workaround :), if not post here, we will try something

---

