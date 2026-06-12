---
title: "detecting wireless adapter"
date: 2008-09-26
forum: General Help
---

### Post by hirohitosan on 2008-09-26
Hi there.
How can I detect my hardware in Ubuntu. I mean something like "Device Manager" in win.
I don't know the manufacturer of my wireless device

thanks

---

### Post by Kevbert on 2008-09-26
You can find out about your wireless by entering the following in terminal
```
lshw -C network
lspci
```
If you require a Device Manager you can go into Synaptic and search for gnome-device-manager.

---

