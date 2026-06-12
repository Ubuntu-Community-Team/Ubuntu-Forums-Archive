---
title: "Open source driver Vs. Closed source driver?"
date: 2021-02-15
forum: Hardware
---

### Post by username2758 on 2021-02-15
Hiya!

How to check if Ubuntu 20.04 LTS is using an open source driver or a closed source driver for AMD graphics?

Thanks!

---

### Post by CelticWarrior on 2021-02-15
No need.

AMD drivers are open-source since many years ago.

---

### Post by QIII on 2021-02-15
AMD graphics on Linux use amdgpu -- open source developed by AMD -- or radeon -- open source, developed by the community with AMD's help.  Each supports a different group of physical GPUs.

Which is used is determined at install time and the correct module is loaded.  There is nothing for you to worry about.

Just as an aside, however, AMD has a proprietary overlay/add-on to amdgpu, which is called AMDGPU-PRO.  That is really unnecessary for the vast majority of users and only works with certain GPUs.

---

### Post by rbmorse on 2021-02-15
One thing to note, however, is that because of the different development schedules it may take some time before the driver updates for the latest AMD graphics hardware are actually available through the repositories of your Linux distro of choice.   

It's always a good idea to ask about specific hardware...in my case, I'm not sure where Ubuntu 20.10 is in terms of drivers for the latest generation of AMD's GPUs (6700,6800 and XT variants).

---

### Post by username2758 on 2021-02-15
Thanks!

I was also wondering how can one see GPU utilization on Ubuntu just like the Task Manager on Windows 10.

Are there any terminal commands or application for that?

Edit: @rbmorse it's Vega 11 Graphics. This is an AMD Ryzen 5 3400GE APU.

---

### Post by mastablasta on 2021-02-16
you are using AMDGPU driver. if you see a display (desktop), then it is utilised.

if you want to measure performance you can use phoronix test suite. it comes with a bunch of benchmark tests.

drivers for vega are in built into kernel because they are opensource.

here is a bit more information on the kernel switches and links to a few GUI apps: [https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)

in short - if you like graphs:
WattmanGTK — A GTK GUI tool to monitor your GPU's temperatures P-states
TuxClocker — A Qt5 monitoring and overclocking tool.

---

### Post by username2758 on 2021-02-16
> **mastablasta said:**
> you are using AMDGPU driver. if you see a display (desktop), then it is utilised.

if you want to measure performance you can use phoronix test suite. it comes with a bunch of benchmark tests.

drivers for vega are in built into kernel because they are opensource.

here is a bit more information on the kernel switches and links to a few GUI apps: [https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)

in short - if you like graphs:
WattmanGTK &#8212; A GTK GUI tool to monitor your GPU's temperatures P-states
TuxClocker &#8212; A Qt5 monitoring and overclocking tool.
Thanks! But I really wanted to learn how to identify which graphics driver is installed on Linux since there is not only AMD.

Would it be "lspci" in terminal?

---

### Post by rbmorse on 2021-02-16
The inxi utility (apt install inxi)  run with the -G switch will show you that.

---

### Post by username2758 on 2021-02-17
> **rbmorse said:**
> The inxi utility (apt install inxi)  run with the -G switch will show you that.

Wow, thank you very much! This tool is great!

Ubuntu 20.04 LTS output:
```
Graphics:
Device-1: AMD Picasso driver: amdgpu v: kernel 
Display: x11 server: X.Org 1.20.9 driver: amdgpu 
resolution: 1920x1080~60Hz 
OpenGL: renderer: AMD Radeon Vega 11 Graphics (RAVEN DRM 3.38.0 
5.8.0-43-generic LLVM 11.0.1) 
v: 4.6 Mesa 21.1.0-devel (git-9bf8bfe 2021-02-12 focal-oibaf-ppa)
```

Lubuntu 20.04 LTS output:
```
Graphics:
Device-1: AMD Picasso driver: amdgpu v: kernel 
Display: x11 server: X.Org 1.20.9 driver: amdgpu [B]FAILED: ati 
unloaded: fbdev,modesetting,vesa resolution: 1920x1080~60Hz[/B] 
OpenGL: renderer: AMD RAVEN (DRM 3.35.0 5.4.0-65-generic LLVM 11.0.0) 
v: 4.6 Mesa 20.2.6
```

Why is inxi giving me these errors on Lubuntu? :roll:

---

