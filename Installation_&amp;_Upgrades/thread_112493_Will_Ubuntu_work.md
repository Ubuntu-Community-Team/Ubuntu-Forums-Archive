---
title: "Will Ubuntu work?"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by Jammy_Stuff on 2006-01-04
After my Ubuntu CDs arrived today, I tried to boot into the Live CD (using a nVidia GeForce 6600). I just got a lod of vertical, orange and brown lines. Firstly then, does anyone know how to get this to work.

Secondly, will it work when I install Ubuntu?

---

### Post by Omnios on 2006-01-04
The vertical lines sound like the vidoe config for the vid driver are off, usually driving the monitor higher than it should be. This can be corrected by manualy setting the frequency range in monitor settings in the Xorg. Not shure how to do that with the live CD but had a similar problem with another computer and just lowered the monitor ranges till it looked ok. Best thing is to get the make and model and get the normal settings off the interenet or off the back of the monitor if there there.

---

### Post by Jammy_Stuff on 2006-01-04
Okay then. Doing dpkg-reconfigure xserver-xorg doesn't work so can someone that has a nvidida GeForce 6600 (or GT) tell me what driver they are using in xserver?

---

### Post by Omnios on 2006-01-04
The default driver for nvidia grapics is nv which I had a problem with with my old monitor that I just replaced. I solved that problem buy adding extra repositories and installing nvidia-glx with apt-get install. This is the driver recomended after install to get glx.

---

### Post by Jammy_Stuff on 2006-01-04
*Installs ndiswrapper using command line* Is the nvidia-glx in the universe?

---

### Post by Omnios on 2006-01-04
Its listed as restricted in synaptic.

---

