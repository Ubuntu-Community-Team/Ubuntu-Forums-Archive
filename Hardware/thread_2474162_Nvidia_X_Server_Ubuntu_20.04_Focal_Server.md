---
title: "Nvidia X Server Ubuntu 20.04 Focal Server"
date: 2022-04-22
forum: Hardware
---

### Post by outlaw67 on 2022-04-22
When using nvidia x i can make changes to control my fan speed but when I reboot my PC the changes are lost ? Or is there other ways to make changes to fan speed ?

---

### Post by TheFu on 2022-04-22
Ubuntu Server doesn't have X/Windows or Wayland.  Linux "Servers" have a console/ptty login only.

The way I control fan speeds is through the BIOS. It has a number of different controls based on the temperature sensors that the BIOS knows about to control fan speed.

According to a man-page search, there's an nvidia tool -  
```
NAME
       nvidia-persistenced  -  A daemon to maintain persistent software
       state in the NVIDIA driver.
```

Farther down in the manpage, it says that configuration is required and provides a file with example startup scripts.  After that is setup, it seems that **nvidia-settings** can control the fan.  My nvidia GPU doesn't have a fan. It is passively cooled, so I can't test anything.

But if you are running a server, there really shouldn't an GUI.

---

