---
title: "Ubuntu can't use my AMD graphics card."
date: 2021-02-14
forum: Hardware
---

### Post by icarolenine on 2021-02-14
Hello guys,

I'm Icaro and I'm running Ubuntu 20.04 on a Lenovo laptop. There are two GPUs in it, an Intel and AMD one. For some reason, I can't choose the AMD one as my main graphics card and I don't seem to find the drivers for it. When I hit ```
sudo lshw -C video
```, this is what I get.

*-display                 
       description: VGA compatible controller
       product: HD Graphics 5500
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:51 memory:d0000000-d0ffffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff
  *-display
       description: Display controller
       product: Venus XTX [Radeon HD 8890M / R9 M275X/M375X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 81

What can I do guys? On Windows I could use that card to play games and stuff and now I can only use the weak Intel one instead....

---

### Post by mastablasta on 2021-02-15
you need to use xrandr and prime. 

See here for more information (the final post explains it):
[https://askubuntu.com/questions/1038271/intel-amd-hybrid-graphics-ubuntu-18-04](https://askubuntu.com/questions/1038271/intel-amd-hybrid-graphics-ubuntu-18-04)

basically the GPu doesn't switch automatically based on the application you run. You need to tell it manually (add command to launcher) to switch to discrete GPU when you need power. and you use PRIME for that: [https://wiki.archlinux.org/index.php/PRIME](https://wiki.archlinux.org/index.php/PRIME)

---

### Post by icarolenine on 2021-02-15
Thank you so much, Mastablasta. You pointed me to the direction that I needed to take to solve the issue. I tried find something relevant for it but with no avail. The current drivers are kinda slow and underperform the Intel graphics. I'm pretty sure this is a drivers thing. Would I benefit from Oibaf's drivers better than the stock ones?

---

### Post by Yellow Pasque on 2021-02-15
I've seen lots of complaints about performance of the AMD GPU in an Intel/AMD hybrid setup. Unfortunately, I haven't seen any solutions.

---

### Post by QIII on 2021-02-15
> **icarolenine said:**
> Would I benefit from Oibaf's drivers better than the stock ones?

In short, no -- despite the myth.  

For your AMD hardware, there are two drivers available:  amdgpu and radeon.  Which is used is determined at install time by which supports your hardware.  Each is actually a kernel module.

What Oibaf does you can do by adding some already available packages -- leaving YOU in control.

The industry does not support Linux well with regard to hybrid graphics.  Depending on how old your laptop is, what typically works best at this point is turning off one or the other in BIOS.

---

### Post by mastablasta on 2021-02-16
> **icarolenine said:**
> The current drivers are kinda slow and underperform the Intel graphics. I'm pretty sure this is a drivers thing. Would I benefit from Oibaf's drivers better than the stock ones?

adding oibaf won't improve it much if any. it is /was mostly there to support newer hardware. but with 20.04 you already have a lot newer kernel than you chip is.

make sure AMDGPU driver is used when you switch. i ran radeon GPU driver and still do on a laptop. they are slightly worse (5 - 10%?) than on windows, but on the other hand linux takes up a lot less ram, so overall there shouldn't be a major difference. AMDGPU on Ryzen is as good as it is on windows. again linux using up less ram, so many games work well. i never tried a hybrid GPU (intel/AMD or intel/nvidia).

both radeon and AMD have various kernel switches that could be used. they can be used to boost or to degrade performance. depending what you do and how you do it. with dual GPU it makes it a bit harder as you don't immediately know if the switch was actually used on correct chip. 

you would use prime command to add it to driver before chip is ran?!? i don't know exactly.

here is some more info on AMDGPU & radeon drivers and their additional libraries (again arch wiki):  [https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)

AMDGPU switches: [https://dri.freedesktop.org/docs/drm/gpu/amdgpu.html](https://dri.freedesktop.org/docs/drm/gpu/amdgpu.html)

and there is also Xorg or Weyalnd compositor.

Xorg is old & quite mature, Weyalnd (default in Ubuntu) is new. try Xorg, it might work better on older hardware.

---

### Post by icarolenine on 2021-02-18
Best community ever! I'll see what I can do. Thanks guys!

---

