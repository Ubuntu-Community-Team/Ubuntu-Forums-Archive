---
title: "Fresh ubuntu installation doesn´t work with RTX 3060"
date: 2023-11-19
forum: Hardware
---

### Post by ecome2 on 2023-11-19
I deleted my Ubuntu 22.04.3 LTS and reinstalled it (with the box ticked for automatically installing drivers), but I still get the Error msgs: "Failed to Allocate NvKmsKapiDevice" and "Failed to register device" while booting.
Ubuntu still starts after the Error msgs but only 1 of my 3 Monitors is  detected and i can only select the resolution 1024 x 768 for it.
Ubuntu worked fine with my old GTX 1060. The RTX 3060 causes no problem in Windows 10.

Did someone have a similar problem and knows how to fix it? If not, does someone know a Linux distribution that works well with the RTX 3060 (best case a beginner friendly distribution :D)?
Thanks in advance!

---

### Post by Autodave on 2023-11-19
What driver is installed for the GPU?  You can find that by clicking on the nVidia icon.

---

### Post by Tadaen_Sylvermane on 2023-11-19
Try logging in with Xorg instead of Wayland? Fairly certain that is still a big problem for Nvidia. Change at the gear on the bottom right I believe.

---

### Post by ecome2 on 2023-11-19
Thanks for the quick response!
Wayland doesn´t seem to start at all. I think Xorg is the one I used before.
A bunch of driver version were installed automatically, im currently using "NVIDIA driver metapackage by nvidia-driver-535", but I´ve already tried the versions 470, 525 and 510 aswell.

---

### Post by ecome2 on 2023-11-19
I FOUND THE PROBLEM! :D
Thank you for the tip with the driver version. I dug a bit deeper into the internet and found a website recommending the version 545 ([https://tutorialforlinux.com/2021/03/23/geforce-rtx-3060-ubuntu-20-04-driver-installation-guide/2/](https://tutorialforlinux.com/2021/03/23/geforce-rtx-3060-ubuntu-20-04-driver-installation-guide/2/)). With this one everything works perfectly!

---

