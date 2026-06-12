---
title: "NVidia 9600 Card Problem"
date: 2009-07-03
forum: Hardware
---

### Post by marque on 2009-07-03
My system:
AMD 64 x3 6000
ASUS MoBo 3N78 Pro
NVIDIA 9600 GSO
Ubuntu 9.04

Video outputs:
On board VGA with standard connections
NVidia card with dual DVI connections and one TV output

Monitor:
Acer 22" LCD with both VGA and DVI inputs

NVidia Hardware driver:
185.18.14


My problem:
If I connect the monitor to the VGA input all seems normal, but if I attempt to use the DVI connection there is no signal.

I have made numerous attempts find a solution such as installation of NVidia Hardware driver version 180 with Ubuntu and with Envy as well as many variations of manual edits to the xorg.conf file.  Everything leads back to the same result, VGA output but no DVI output.

What I want is simple, to get a single DVI signal to this monitor.  (For the moment I am not concerned with dual monitors or TV out)

This is a newly built machine.  If necessary I am willing to reinstall hardware drivers or the entire OS.


Can someone suggest to me what I can try that will get signal from the DVI ports of this NVidia card?

---

### Post by glennric on 2009-07-03
If you connect your monitor to the dvi connection when you are booting the computer do you see anything then, or is this just after linux starts that you are having the problem?

---

### Post by marque on 2009-07-03
If I boot with only the DVI connected all I get is a blank screen, simply no signal.  

Apparently there is power to the NVidia card as the light on the card is working.

---

### Post by glennric on 2009-07-03
Have you set your bios to use the pci video card?

---

### Post by marque on 2009-07-03
I figured it out.  After all that work I simply neglected to connect power to the video card board.

And I always thought of myself as a detail person.

Y'all have good laugh on me!

Thanks

---

