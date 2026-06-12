---
title: "Switching back to nvidia card not possible prime problem. Kubuntu 18.04LTS"
date: 2018-05-20
forum: Hardware
---

### Post by berghopper on 2018-05-20
[kubuntu 18.04LTS] After installing ppa nvidia-390 graphics drivers, switching to intel graphics card results in nvidia drivers not being loaded at all.


When switching prime profiles with the Nvidia x-server settings to internal intel graphics card, I am unable to switch back to the dedicated graphics card.
This is in part because the Nvidia driver does not load at all. The only error I get is the following while trying to start the nvidia x-settings;


```
~$ nvidia-settings
ERROR: NVIDIA driver is not loaded
ERROR: Unable to load info from any available system 
```


specs;
(NEOFETCH)


ccpeters@ccpeters-Lenovo-ideapad-510-15ISK 
------------------------------------------ 
OS: Ubuntu 18.04 LTS x86_64 
Host: 80SR Lenovo ideapad 510-15ISK 
Kernel: 4.15.0-20-generic 
Uptime: 17 mins 
Packages: 2465 
Shell: bash 4.4.19 
Resolution: 1920x1080 
DE: KDE 
WM: KWin 
Theme: Breeze [KDE], Breeze [GTK3] 
Icons: Breeze [KDE], Breeze [GTK3] 
Terminal: konsole 
CPU: Intel i7-6500U (4) @ 3.100GHz 
GPU: NVIDIA GeForce 940MX 
GPU: Intel Integrated Graphics 
Memory: 857MiB / 7882MiB 


I'm using kde plasma 5.12 on kubuntu 18.04 LTS, with the nvidia-390 drivers.
I have overall noticed a lot of bugginess with nvidia under the new ubuntu 18.04 and have seen many bug reports of other people having problems as well.
This is probably completely nvidia's drivers fault.

---

