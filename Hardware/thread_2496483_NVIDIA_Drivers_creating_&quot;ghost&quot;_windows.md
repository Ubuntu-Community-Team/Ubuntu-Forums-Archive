---
title: "NVIDIA Drivers creating &quot;ghost&quot; windows"
date: 2024-03-30
forum: Hardware
---

### Post by pecoflyer on 2024-03-30
Hello
using Xubuntu 20.04 LTS I have trouble with my NVIDIA graphics card GeForce GTX 1060 6GB ( see attached)
Tried
sudo apt update

sudo sudo apt purge nvidia*

sudo ubuntu-drivers autoinstall
(also tried sudo apt install nvidia-driver-530)

and reboot, but no success, still having the same problem
Any help much appreciated. Thanks

---

### Post by MAFoElffen on 2024-03-31
You didn't say which drivers you have tried... except nvidia-driver-530.

---

### Post by Yellow Pasque on 2024-04-01
Any way you can try another desktop to see if the issue occurs there? I haven't used Nvidia for a while, but I remembering preferring compton/picom compositor for Nvidia instead of xfwm's built-in compositor.

---

### Post by MAFoElffen on 2024-04-01
For your GPU, I would have suspected that you would have tried nvidia-driver-525 & nvidia-driver-535... and the  -open or -server variants of those. Those seem to work best for me. -545 just has had some patches that have fixed some problems where it is getting stable for Linux. -550 is still working things out in a few areas.

Honestly, I have used NVidia with Unix and Linux since 2005. There are so many hardware combinations and software rendering combinations that users "use" that affect that (different games, different desktops, different rendering engines), that the best way I have found is to try different drivers and see what works best for the hardware combination in sort of a trial and error affair. I can recommend what works best for me, but that may vary of your own hardware combination.

---

### Post by pecoflyer on 2024-04-01
Thanks for all the answers. I tried version 530 - 470 - 525 - 515 - 510 and 440 and the problem stayed. I don't know where I can find 535 as ubuntu-drivers version command did not return anything higher than the recommended and tested 530 version. I suppose I'll have to try them one by one although in some cases I got very rare results

---

