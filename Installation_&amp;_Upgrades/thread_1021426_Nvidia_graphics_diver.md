---
title: "Nvidia graphics diver"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by zapree on 2008-12-25
So i have an Nvidia GeForce series 7 card and the problem that i have is that the driver that ubuntu looks up automatically does not work properly giving me only a 670*300 resolution or something along those lines, until now i never had a problem but for christmas i got a monitor with 1360*700 resolution and i had to disable the driver to even be able to use ubuntu, is there a way to find the right driver that i need??
Thanks Patrick

---

### Post by Partyboi2 on 2008-12-27
You should be able to go to System>Admin>Hardware Drivers and enable the nvidia driver then go to System>Admin>NVIDIA X server settings and change the resolution. If NVIDIA X server settings is not there you can install by opening a terminal and
```
sudo apt-get install nvidia-settings
```

---

