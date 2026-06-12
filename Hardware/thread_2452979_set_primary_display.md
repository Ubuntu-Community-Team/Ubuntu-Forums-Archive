---
title: "set primary display"
date: 2020-10-31
forum: Hardware
---

### Post by chinasky on 2020-10-31
Hello,

How can I set my amd graphics card as primary instead of the intel hd4600?   ( I know that can be done in bios but I'm interested in configure it using xorg)

Thank you

---

### Post by Deep_Peasant on 2020-10-31
:confused: You are running a dedicated amd graphics card and using the integrated intel gpu... I want to know that trick too. 
You must have set the bios to use the integrated intel hd4600 otherwise there is no way I know off how it could be used by the os.
Therefore the amd card will never be detected, it's not set as the primary in the bios, it doesn't exist to the os/system. The bios doesn't 
report it to be there to the os. I think.

---

### Post by chinasky on 2020-11-01
I finally did it:

boot your pc with amd graphics as primary in bios

kill x server and then run Xorg -configure

copy xorg.conf.new to /etc/X11 (as xorg.conf)

Reboot and change intel graphics as primary in bios

---

### Post by Deep_Peasant on 2020-11-01
> **chinasky said:**
> I finally did it:

boot your pc with amd graphics as primary in bios

kill x server and then run Xorg -configure

copy xorg.conf.new to /etc/X11 (as xorg.conf)

Reboot and change intel graphics as primary in bios

So you managed to set the amd as primary display even with the intel set in bios.
Why do you want to do that?
This is a recipe for disaster in my book :D
I'm curious what hardware you pulled this off. 
And I'm wondering how long xorg.conf will keep the setting.

---

### Post by MartyBuntu on 2020-11-01
What is the model of the laptop?

---

### Post by Deep_Peasant on 2020-11-01
> **MartyBuntu said:**
> What is the model of the laptop?

Oh darn it, you think it's a laptop with 'dual-graphics' ugh, meh. Even worse they call it a 'dual graphics SOLUTION'  :mrgreen:

---

### Post by MartyBuntu on 2020-11-02
> **Deep_Peasant said:**
> Oh darn it, you think it's a laptop with 'dual-graphics' ugh, meh. Even worse they call it a 'dual graphics SOLUTION'  :mrgreen:

It has to be a laptop.
Otherwise, the graphics card you'd be using is the one your cable would be plugged into.

---

### Post by CelticWarrior on 2020-11-02
> **MartyBuntu said:**
> It has to be a laptop.
Otherwise, the graphics card you'd be using is the one your cable would be plugged into.

Not necessarily.
Multi-monitor is a feature in some high-end motherboards - enables simultaneous monitors connected to different graphics cards - and, in compatible desktops, the usage of a dGPU for machine learning alongside with the iGPU drawing the desktop area (or two independent dGPUs) is pretty common. By "compatible" I mean the ones with a motherboard that allow the simultaneous usage of multiple cards. Entry level hardware typically disables the iGPU in the presence of a dGPU.

What has been asked here though seems nonsensical at first glance.

---

### Post by MartyBuntu on 2020-11-02
> **CelticWarrior said:**
> Not necessarily.
Multi-monitor is a feature in some high-end motherboards

What motherboard outputs both AMD and Intel video?

> **CelticWarrior said:**
> 

What has been asked here though seems nonsensical at first glance.

No arguement.

---

### Post by CelticWarrior on 2020-11-03
> **MartyBuntu said:**
> What motherboard outputs both AMD and Intel video?

[https://forums.tomshardware.com/threads/multiple-monitors-using-outputs-from-gpu-and-motherboard.1400815/](https://forums.tomshardware.com/threads/multiple-monitors-using-outputs-from-gpu-and-motherboard.1400815/)

---

