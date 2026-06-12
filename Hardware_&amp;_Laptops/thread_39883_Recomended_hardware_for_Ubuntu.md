---
title: "Recomended hardware for Ubuntu"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by pedromperez80 on 2005-06-06
I' would like to know the recomended hardware ro run Ubuntu, wich configuration is the optimal on the x86 plataform, what are your suggestions?

Pedro Pérez

---

### Post by tread on 2005-06-06
[http://www.ubuntulinux.org/wiki/HardwareSupport](http://www.ubuntulinux.org/wiki/HardwareSupport)

---

### Post by PryGuy on 2005-06-07
Defenitely I'm sure that in case with Ubuntu "recommended" doesn't mean "modern"... I have ASUS P4GPL-X motherboard which is pretty new, it has Azalia ALC880 High Definition Audio Codec and Marvell Yukon Gigabit LAN. And I had to compile the both drivers for Ubuntu (Windows has no support for it as well, but the installation procedure is way easier).

So I believe the "ideal" configuration will be something like nVidia Geforce FX (Ubuntu doesn't seem to support ATI just fine) for graphics, good old AC'97 for sound and a typical Realtek LAN network card which is a very cheap and wide spread thing nowadays.

Not so sure about the sound, but sure about the other components. LAN works out of the box and it's very easy to enable a 3D hardware support for nVidia:```
sudo apt-get install nvidia-glx
sudo /etc/init.d/gdm stop
sudo nvidia-glx-config enable
sudo gdm
```

---

