---
title: "AMD Radeon RX 6600 GPU on Ununtu Desktop 24.04"
date: 2024-07-07
forum: Hardware
---

### Post by tedman2 on 2024-07-07
I am thinking of buying the AMD Radeon RX 6600 GPU for Ubuntu Desktop 24.04

Looking around the internet there appears to be problems with AMD drivers.
I thought that the driver problem was mostly confined to NVIDIA.

At the moment I am using the NVIDIA GTX 960 GPU, and the fans are constantly full blast with the X.org driver.
Things are little bit stuttery with this driver.
But with the proprietary NVIDIA driver the resume function does not work.

I am very new to Linux/Ubuntu and it has been suggested to me that AMD GPU drivers have greater compatibility with Linux.

Can anyone give me some info about this ?

---

### Post by Yellow Pasque on 2024-07-07
> **tedman2 said:**
> Looking around the internet there appears to be problems with AMD drivers.

Link(s)? Ubuntu 24.04 supports the RX6600 with the appropriate kernel, 3D, and video decode drivers. That doesn't guarantee it's bug free, but if you want useful feedback, you're going to have to be more specific about these "problems".

---

### Post by easydawg on 2024-07-07
AMD GPU's are supposed to run just fine without running any proprietary drivers but on the AMD website for Drivers it actually calls out Ubuntu 22.04.4 so if the drivers are made for 22.04 then 22.04 must be good for these AMD Drivers. 24.04 I would think should be the same.

[https://www.amd.com/en/support/downloads/drivers.html/graphics/radeon-rx/radeon-rx-6000-series/amd-radeon-rx-6600.html](https://www.amd.com/en/support/downloads/drivers.html/graphics/radeon-rx/radeon-rx-6000-series/amd-radeon-rx-6600.html)


Here's the install page where you may be able to learn more:

[https://amdgpu-install.readthedocs.io/en/latest/](https://amdgpu-install.readthedocs.io/en/latest/)

---

### Post by Shibblet on 2024-07-08
> **tedman2 said:**
> I am thinking of buying the AMD Radeon RX 6600 GPU for Ubuntu Desktop 24.04
Looking around the internet there appears to be problems with AMD drivers.
I thought that the driver problem was mostly confined to NVIDIA.
I have a 6600M built into my Mini-PC.  The only problem that I have, is that I have to disable the iGPU (Ryzen 5900HX) in the BIOS so that it doesn't conflict with the dGPU (6600M).  So, if you have a Ryzen CPU, make sure you disable the iGPU.

> **tedman2 said:**
> At the moment I am using the NVIDIA GTX 960 GPU, and the fans are constantly full blast with the X.org driver.
Things are little bit stuttery with this driver.
But with the proprietary NVIDIA driver the resume function does not work.

I am very new to Linux/Ubuntu and it has been suggested to me that AMD GPU drivers have greater compatibility with Linux.
Kinda.  Now that Nvidia has open-sourced their drivers, it's a whole new ball-game.
Currently though, AMD drivers are included in the Kernel, and will work by default (in most cases).  This means, you don't even have to install drivers (again, in most cases.)
> **tedman2 said:**
> Can anyone give me some info about this ?
I can play just about anything in 1080p (High, or Ultra) between 45-60fps.
If I get a little picky about the options, I turn a few down to medium, I can get 72-120fps.
This is on some high-end games.  Marvel's Guardians of the Galaxy, Horizon Zero Dawn, Remnant: From the Ashes
Of course, each game is different.

---

### Post by tedman2 on 2024-12-01
Just placed my order for the ASUS AMD RX 6600 8GB
I think it's going to do what I need.

---

