---
title: "Fix for NVIDIA driver for 32 bit (x86) Karmic Koala (9.10) and Quadro FX 500/600"
date: 2009-12-23
forum: Hardware
---

### Post by cbrinegar on 2009-12-23
After many searches on these forums and other sites, I have come to the conclusion that not many people have reported this specific problem (though many have had other nvidia driver issues).

I have tried the 173.14.20 and 185.x drivers from the Ubuntu repositories, and neither work with this card.  However, completely uninstalling all of the nvidia drivers from the repository and installing 173.14.22 from the NVIDIA website works great.  Here is the procedure:

Completely uninstall all nvidia drivers using Synaptic
Download NVIDIA-Linux-x86-173.14.22-pkg1.run
Ctrl+Alt+F1 to get to a text login
Log in
sudo service gdm stop
sudo sh NVIDIA-Linux-x86-173.14.22-pkg1.run
sudo service gdm start
(Ctrl+Alt+F7 to go to graphical login if it doesn't switch automatically.)

---

