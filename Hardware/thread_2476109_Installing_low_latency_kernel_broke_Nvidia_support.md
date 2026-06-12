---
title: "Installing low latency kernel broke Nvidia support"
date: 2022-06-16
forum: Hardware
---

### Post by halfbeing on 2022-06-16
I am running Ubuntu 22.04. I installed the low latency kernel and that broke support for my Nvidia card. Neither when booting into the low latency kernel nor the generic kernel can I get a resolution better than 640x480. How can I fix this?

---

### Post by #&amp;thj^% on 2022-06-16
first, do you have the necessary kernel headers and modules installed, and how did you install nvidia?
show this please:
```
modinfo nvidia
```
and:
```
sudo dkms status
```
Are you using Gnome-Wayland?

---

