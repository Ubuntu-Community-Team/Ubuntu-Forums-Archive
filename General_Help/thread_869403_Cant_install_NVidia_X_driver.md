---
title: "Cant install NVidia X driver"
date: 2008-07-24
forum: General Help
---

### Post by knudsenjoe on 2008-07-24
I have the nvidia 'latest' drivers on my hardy system. I think the xxxxxx-19 Linux kernel update broke my video. I can't change resolution. I have nvidia-settings, but when I try to configure them, I get:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I've tried the above solution, it backs up the file and seems to write another. But when I restart I'm still stuck in 800x600 mode. Please help.

---

### Post by overdrank on 2008-07-24
> **knudsenjoe said:**
> I have the nvidia 'latest' drivers on my hardy system. I think the xxxxxx-19 Linux kernel update broke my video. I can't change resolution. I have nvidia-settings, but when I try to configure them, I get:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I've tried the above solution, it backs up the file and seems to write another. But when I restart I'm still stuck in 800x600 mode. Please help.

Hi and have you tried to manually install the driver again?

---

### Post by drs305 on 2008-07-24
I have had excellent results using EnvyNG. You install it with:
```
sudo apt-get install envyng-gtk
```

Run it: System Tools >  EnvyNG.

Select Nvidia drivers and Install Nvidia Driver (automatic).

---

