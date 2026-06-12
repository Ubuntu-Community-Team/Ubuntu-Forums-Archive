---
title: "Cant Install Nvidia Graphics Propritary Driver"
date: 2008-12-07
forum: Hardware
---

### Post by PressureWave on 2008-12-07
Im using Ubuntu 8.10 and i am trying to install an Nvidia Geforce FX GO 5200, I'm attempting to install my Nvidia Graphics card, but whenever i go to the Hardware driver window i hit activate, it asks for my password and says downloading and then just goes back to the first screen. I'm not sure what to do.

[IMG]http://i44.photobucket.com/albums/f9/laserskys/HardwareDriver-3.jpg[/IMG]

---

### Post by Ayuthia on 2008-12-07
You might try going into Synaptic and install the nvidia driver through there.  It should be called nvidia-glx-173.  After it is installed, you might want to check and see if nvidia-settings was installed.  That application comes in handy sometimes when you want to configure your graphics card to use dual-monitors.

---

### Post by bdoe on 2008-12-07
I had this problem when installing Intrepid on a pair of computers - one with an ATI card, the other with an nVidia card. The solution for me was to make sure all the repositories were enabled in software sources, and then running the update manager. At issue seems to be an older restricted-software package in the shipped version of Intrepid. Updating the restricted software package made the Restricted Driver Manager work again.

As an alternative, you could install the Envy package, and let Envy handle finding and installing the drivers.

---

### Post by PressureWave on 2008-12-07
ok ill give it a shot

---

