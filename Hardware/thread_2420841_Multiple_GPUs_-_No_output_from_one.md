---
title: "Multiple GPUs - No output from one"
date: 2019-06-11
forum: Hardware
---

### Post by crono1412 on 2019-06-11
Hey all,

I have a bit of a unique situation.  I am trying to set up my Ubuntu headless server for GPU passthrough with the ultimate goal of having the server act as multiple gaming PCs which are accessed through steam link.  There are lots of hurdles there, but the specific problem I'm having is fundamentally a hardware problem.

For GPU passthrough to work, you need more than one GPU.  One dedicated to the host system, and the other passed through to the guest system.  As such I have a Geforce GT 710 (PCIe 1X card), and a Geforce GTX970.  Video for X server and console output only comes out of the 970.  This is a problem because when I capture the 970 with VFIO, the display stops working (or rather, is blank).  Moving my cable over to the GT710 results in no signal, as if the card isn't even working.  I know it works though, because in the absence of the 970 being installed, it works just fine.

I should also note that the system bios boot screen only shows up when the monitor is connected to the 970 as well.

I'm trying to figure out why this is happening, and try and make the GT710 the primary graphics card for X and for terminal output.

My relevant output from inxi -Fxz is below

```
Graphics:  Device-1: NVIDIA GM204 [GeForce GTX 970] vendor: Micro-Star MSI driver: vfio-pci v: 0.2 bus ID: 01:00.0            Device-2: NVIDIA GK208B [GeForce GT 710] vendor: ZOTAC driver: N/A bus ID: 05:00.0 
           Display: tty server: X.org 1.20.4 driver: fbdev,nouveau unloaded: modesetting,vesa tty: 152x56 
           Message: Advanced graphics data unavailable in console. Try -G --display 
```

I notice that there is no driver loaded for the GT710.  But when I run sudo ubuntu-drivers devices, I only get output for the 970:

```
== /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0 ==modalias : pci:v000010DEd000013C2sv00001462sd00003161bc03sc00i00
vendor   : NVIDIA Corporation
model    : GM204 [GeForce GTX 970]
driver   : nvidia-driver-418 - distro non-free recommended
driver   : nvidia-driver-390 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
```

So I don't even have the option to assign a driver for the 710.  I think this might be the core of my issue.  Once this is solved, I still need to find out how to assign the GT710 as the primary display adapter for terminal and X output.  I've seen plenty of tutorials on how one would make a second gfx card primary in X, but the terminal output is the bigger problem, in my opinion.

I'll keep searching for a solution while I wait for a reply. Thanks in advance.

EDIT: So I got the driver situation sorted, but still have the problem of the weaker video card producing no output.  in BIOS I have "PCI" selected as primary display (as opposed to PCIe), but that does not solve the problem.

---

