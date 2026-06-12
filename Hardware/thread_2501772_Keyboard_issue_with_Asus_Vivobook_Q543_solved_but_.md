---
title: "Keyboard issue with Asus Vivobook Q543 solved but secure boot incompatibility arises"
date: 2024-10-20
forum: Hardware
---

### Post by firthu on 2024-10-20
The built-in keyboard of the laptop does not work with 24.04 kernel version 6.8. Installing 6.11 manually solves this, but it is not compatible with Secure boot. 
In the latter case (6.11), I get "bad shim signature - you need to load kernel first". Online I found the workaround to disable Secure Boot, which works.
Any possibility to allow Secure Boot? It is useful for dual boot, bitLocker proper functioning

---

### Post by firthu on 2024-10-22
Nvidia and external monitors didn't work. Ubuntu 24.10 USB produced erros. I ended up installing Kubuntu 24.10, and it works fine regarding keyboard and Nvidia.

---

