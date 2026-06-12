---
title: "Problem after installing Nvidia driver"
date: 2024-06-13
forum: Hardware
---

### Post by vahidihooman on 2024-06-13
Hi everyone,
I have installed ubuntu 24.04 on my PC recently. There is a GTX GeForce780ti graphics card on it. I installed Nvidia driver using "Software & Updates" of ubuntu (so as it was recommended, nvidia-driver-470 was installed). Before installing Nvidia driver everything was good. But after that when I resize a window (maximize or minimize it), its icons and writings disappear. When I pull mouse cursor on them (not clicking) they appear again!!
could you please help and guide me?

---

### Post by #&amp;thj^% on 2024-06-13
When you mention Ubuntu, we all assume using Gnome as a Desktop. (Details matter)

So Gnome defaults to a wayland session, and nVidia still has a few rough edges that need to be ironed out, have you tried an X11 session yet?

Also would be nice to see if the drivers installed correctly:
```
apt policy nvidia-driver-470 nvidia-dkms-470
```
And this please:
```
nvidia-smi
```

---

### Post by vahidihooman on 2024-06-13
Thanks a lot for reply
I used two ways to install Nvidia driver: by "Software & Update" and by runfile. Before installing driver I done all of pre-installation steps according to official Nvidia  documentation such as installing necessary libs and blacklist nouveau. After each of ways, I checked that installation was done correctly, for example "nvidia-smi" that you mentioned. Installations were successful but the problem still existed. How I can change session to X11? Is it possible I can return to default options?

---

### Post by tea for one on 2024-06-13
> **vahidihooman said:**
>  How I can change session to X11?
Log out and select xorg session from gear wheel icon
Please see attachment

---

