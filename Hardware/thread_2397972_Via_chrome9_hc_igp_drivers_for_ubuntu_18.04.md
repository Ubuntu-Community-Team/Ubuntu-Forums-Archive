---
title: "Via chrome9 hc igp drivers for ubuntu 18.04"
date: 2018-08-06
forum: Hardware
---

### Post by kumarayush2102 on 2018-08-06
I have an old pc with amd sempron 2800+ single core 1.6ghz , 1.5 gb of ram, 160 gb of hdd, and via k8m890ce chipset, this pc support vista , i want to switch to ubuntu but the problem is resolution is stucked at 640x480 


I solved it but the graphics is lagging and some times when i open a app i can see only a white screen, i want to install its driver

Please help me

Thanks in advance

---

### Post by deadflowr on 2018-08-06
Your machine is too weak to run proper Ubuntu.

But you might get in to work well with a lighter variant such as Lubuntu or Xubuntu
[https://xubuntu.org/download]("https://xubuntu.org/download")
[https://lubuntu.me/downloads/]("https://lubuntu.me/downloads/")

Then try installing the openchrome driver
in a terminal
```
sudo apt install xserver-xorg-video-openchrome
```
It's probably the best you can hope for.

---

