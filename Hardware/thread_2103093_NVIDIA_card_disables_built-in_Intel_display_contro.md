---
title: "NVIDIA card disables built-in Intel display controller"
date: 2013-01-09
forum: Hardware
---

### Post by julf on 2013-01-09
Hi!

In hope of a dual-head system, I added a NVIDIA GeoForce GT630 card to my PC (Acer Extensa e470 / E5400, Intel 43 chipset). The new card works just fine, but it seems to diable / block the bililt-in Intel GMA X4500 controller - lspci now only shows the NVIDEA card.

Internal controller is enabled in BIOS. 

Running 12.10. 

Any ideas/suggestions?

---

### Post by vasiliscnisrok on 2013-01-09
NVIDIA + Intel + Ubuntu = 
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by julf on 2013-01-09
> **vasiliscnisrok said:**
> NVIDIA + Intel + Ubuntu = 
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I did come across Bumblebee googling for my problem, but it seems to be for laptops, not desktops - anyway, will try it! Thanks!

---

### Post by Yellow Pasque on 2013-01-09
No, bumblebee is for hybrid/Optimus GPU setups (where the nvidia GPU outputs through the Intel GPU).

You can only choose one GPU. When your computer starts up, it sees the PCI-e card and disables the IGP. If you want dual monitor, you'll have to attach bot of them to the nvidia card.

---

### Post by julf on 2013-01-09
> **Temüjin said:**
> You can only choose one GPU. When your computer starts up, it sees the PCI-e card and disables the IGP. If you want dual monitor, you'll have to attach bot of them to the nvidia card.

Bummer - seems such a waste of a graphics controller!

---

