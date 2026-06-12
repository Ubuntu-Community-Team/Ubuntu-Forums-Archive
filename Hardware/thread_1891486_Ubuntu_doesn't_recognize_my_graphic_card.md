---
title: "Ubuntu doesn't recognize my graphic card"
date: 2011-12-05
forum: Hardware
---

### Post by rock.it on 2011-12-05
Hi everyone!

I need some help here, my Ubuntu 11.10 doesn't recognize my graphic card.

I have the intel drivers installed, please look at the info.txt attached to see the output from *lspci* and *dpkg -l| grep intel*...I can't list here, I don't known why ....

Any ideias???

Tks in advanced!!

---

### Post by phidia on 2011-12-05
This appears to be the section for your gpu: > Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller

How did you install the driver-what specifically are your computer's symptoms and did you use the guide [here]("https://help.ubuntu.com/community/BinaryDriverHowto")?

---

### Post by BicyclerBoy on 2011-12-05
The correct intel driver is open source..i915 (810 - ivy)

check open GL
glxinfo | grep OpenGL

---

### Post by Mark Phelps on 2011-12-06
Ubuntu DID recognize your graphics chipset, otherwise, you would not have a graphical desktop.

So, do you have one of the newer PCs that has switchable graphics, that is, onboard Intel coupled with an ATI or NVidia card?  IF so, this is a very different problem to solve than simply installing other Intel drivers.

---

