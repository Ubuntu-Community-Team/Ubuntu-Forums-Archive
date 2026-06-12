---
title: "Graphic drivers for ATI M"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by NiksaVel on 2006-06-04
Hey all...

yes I'm a n00b and I searched the forums, but I'm just not sure so I'll post a question here:

I have a lap with ATO mobility 9700 graphics card...  the installer went smoothly and ubuntu works and looks fine, although at moments it doesn't seem all to smooth - minimizing/maximizing windows and the like...  so I am not sure if it's using the full potential of the graph. card...    how can I see for sure? 
I see in the device manager that it recognised the card as ATI 9600, but I don't know wether it is using it to it's full potential...  hardware acceleration and all....   

Fedora had a neat little prog displaying monitor and graphics adapter with resolutions and all in the administration menu, is there something like it for ubuntu?


thanks for you help...

---

### Post by nolongerlivecd on 2006-06-04
Terminal, fglrxinfo

---

### Post by NiksaVel on 2006-06-04
fglrxinfo: command not found

---

### Post by kaffelars on 2006-06-04
I also have a 9700 Mobility, in works great.
But to use the ATI drivers you have to install some fglrx-packages in Synaptic.
Do a search for fglrx synaptic and install the correct ones for your kernel.
You'll also have to change from "ati" to "fglrx" in /etc/X11/xorg.conf (search for "driver" in this file.

---

### Post by NiksaVel on 2006-06-04
okay:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


is this in order?

---

### Post by lynng on 2006-06-04
[quote=NiksaVel]okay:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


is this in order?[/quote]

No, not okay.  The above indicates you are using the 2d Mesa drivers for your card.  Meaning you are not getting any 3d graphics acceleration at all.  There are a few howtos posted in the forums.  If you've already installed the fglrx driver packages, what probably happened is that they didn't get completely installed b/c X was still running.  When I got mine working I had to exit the gui and stop X from the command line in order for the drivers to fully install.

---

### Post by NiksaVel on 2006-06-06
okay...  got it working, thnx for the help...

---

