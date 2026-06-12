---
title: "What mininal required VRAM using Ubuntu 20.04 ?"
date: 2022-01-25
forum: Hardware
---

### Post by aug7744 on 2022-01-25
What is the video RAM minimum requirement using Ubuntu 20.04 ?
Thanks for reply.

---

### Post by TheFu on 2022-01-26
Zero.  Use a tty or serial connection.  This is not the default in most installers for most Ubuntu flavors.
Zero would be for a server without a GPU at all.

I have no idea what it is for a GUI with a DE. I've run L/X/*buntu in virtual machines with 64MB of vRAM. I haven't looked at Gnome3+ Ubuntu in years. Same for KDE. I typically don't use any DE, just a light WM in a 64MB VM.

On physical machines, I have nvidia 430GT, GT 1030 and some AMD Ryzen iGPU.  Nothing high-end in the last 12+ yrs.  I did have an nvidia 7200 GS lose support and refuse to go above 1080p resolution, but the card still worked.

---

### Post by antares2328 on 2022-01-26
There's not really a minimum requirements as far as VRAM goes, it depends on your desktop environnement I guess, but you should be able to get by with 128Mb

---

### Post by guiverc on 2022-01-27
This question was asked in a slightly different form (*Lubuntu/LXQt only*) here - [https://discourse.lubuntu.me/t/what-is-the-video-card-vram-requirement-for-lubuntu-20-04/3045](https://discourse.lubuntu.me/t/what-is-the-video-card-vram-requirement-for-lubuntu-20-04/3045) where I state no VRAM requirement exists.

Main **Ubuntu** **Desktop** does however provide some minimums - [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

> 
From 17.10 onwards the desktop uses [GNOME Shell]("https://en.wikipedia.org/wiki/GNOME_Shell"). In order to run these environments the system needs a more capable graphics adapter – see more [here]("https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements") or below: 


[LIST]
[*]4096 MiB RAM (system memory) for physical installs. 
[*]2048 MiB RAM (system memory) for virtualised installs. 
[*]3D Acceleration Capable Videocard with at least 256 MB 
[/LIST]


[LIST]
[*]VGA capable of 1024x768 screen resolution 
[/LIST]


The 256MB video memory doesn't apply to Ubuntu Server 20.04 LTS though.

---

