---
title: "Nvidia powermizer stuck at 1"
date: 2015-12-09
forum: Hardware
---

### Post by niai on 2015-12-09
I recently got a new graphics card for my laptop it seems to be working grand in Windows.

Drivers have installed fine in Ubuntu and the laptop is working but I am getting very low FPS in Heaven benchmark and the powermiser level will not move off of 1, if i change the drop down to performance it dose not change, I have tried adding things to xorg.conf but nothing.

I have 3 level displayed in the settings 0 1 and 2.

Its a Alienware M17Xr3 with a 580m in it currently running Ubuntu-gnome 15.10 I have tried a few other releases and flavors but nothing seems to have worked.

Any help is appreciated

[IMG]http://i.imgur.com/P5RoE1x.png[/IMG]

---

### Post by efflandt on 2015-12-10
Which nvidia driver package are you running?```
dpkg-query -l nvidia* | grep ii
```

---

### Post by niai on 2015-12-10
Using 352.63 from Jockey, its the version the Nvidia site recommends. I have also tried adding the xorg-edgers[SIZE=2] ppa it didnt help.[/SIZE]

```
ii  nvidia-352             352.63-0ubuntu0.15.10.1 amd64        NVIDIA binary driver - version 352.63
ii  nvidia-opencl-icd-352  352.63-0ubuntu0.15.10.1 amd64        NVIDIA OpenCL ICD
ii  nvidia-prime           0.8.1                   amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings        352.21-0ubuntu1         amd64        Tool for configuring the NVIDIA graphics driver
```

Thanks for the reply.

---

