---
title: "Discrete and integrated gpus"
date: 2015-04-09
forum: Hardware
---

### Post by andrehsu6 on 2015-04-09
So I cant find it via google, so here it is:
I have a discrete nvidia gpu, and also an integrated intel gpu.
On windows, you can choose which one to use via right click menu, or the nvidia control panel.
So on ubuntu, which one does it use for the desktop? Can you change the one used on a per application basis? Also, how do you check which one is being how to used right now?

---

### Post by mcduck on 2015-04-09
By default you are going to be using the Intel GPU. 

However you can install the proprietary Nvidia drivers for the discreet GPU, and then use either Bumblebee or nvidia-prime to switch to the nvidia GPU. Bumblebee wil do it per-application, but you'll need to start the  application through bumblebee for it to work (so either starting stuff from command line or creating/modifying custom launchers for things to use it). Nvidia-prime will allow you to select which one is used, either through nvidia's control panel or by installing & using a separate indicator applet for it. The downside is that switching between the GPU's requires you to log out and back to take effect.

---

