---
title: "Screen flickering on low brightness after sleep"
date: 2023-07-02
forum: Hardware
---

### Post by quentinodelavega on 2023-07-02
Hello,

 I've been trying to fix the flickering screen on my notebook (Acer  predator PT516-52S-718U) for a few hours now with no success.

 Problem description :

[LIST]
[*]The screen is working well on first boot, I can control the backlight and I see no flickering (flashes)
[*]After   a suspend (Lid close, hibernate, auto sleep), the screen says black. I   have to increase the brightness with the keyboard so it switches on.   Unfortunatly, at that point, the screen (backlight ?) flickers (rapid   flashes) if I set the brightness under 80%.
[/LIST]
You can find a video of the flashes here : [https://youtu.be/rW7effcvWdA](https://youtu.be/rW7effcvWdA)


The problem has been reproduced on **three** Acer predator PT516-52S-718U and do not appears on Windows (11).
The problem has been reproduced on Linux Mint.

 Specs :

[LIST]
[*]Acer predator PT516-52S-718U
[*]i7-12700H
[*]32go RAM
[*]Nvidia 3070 ti & Integrated intel graphics
[*]Dual boot or not, same thing
[*]Ubuntu 22.04 / updated
[/LIST]
 
My research drove me to play with kernel parameters, Xorg configuration & Bios...

[LIST]
[*]Bios is updated to the last version.
[*]I tried with updated kernel (6.3) with no changes
[*]I tried with and without the nividia-drivers (535) with no success
[*]I tried disabling the nvidia systemctl "suspend / hibernate / resume" with no success
[*]I  tried adding parameters to GRUB : `acpi_backlight=nvidia_wmi_ec  i915.enable_psr=0 i915.enable_dc=0` (and a lot of others parameters with  no succes)
[/LIST]

Some data : 

inxi -G
 	```

Graphics:

  Device-1: Intel Alder Lake-P Integrated Graphics driver: i915 v: kernel
  Device-2: NVIDIA driver: N/A
  Device-3: Quanta Acer FHD User Facing type: USB driver: uvcvideo
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell v: 42.5 driver: X: loaded: intel gpu: i915
    resolution: 2560x1600~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2)
    v: 4.6 Mesa 22.2.5-0ubuntu0.1~22.04.3
``` 
ll /sys/class/backlight/ (on kernel 6.4.0-060400-generic)
```
total 0drwxr-xr-x  2 root root 0 juil.  1 18:09 ./
drwxr-xr-x 87 root root 0 juil.  1 18:09 ../
lrwxrwxrwx  1 root root 0 juil.  1 18:09 nvidia_wmi_ec_backlight -> ../../devices/pci0000:00/PNP0C14:01/wmi_bus/wmi_bus-PNP0C14:01/603E9613-EF25-4338-A3D0-C46177516DB7/backlight/nvidia_wmi_ec_backlight/ 

```(On default kernel, it showed two more backlight (drivers?) : intel_backlight & display_0).

It is a software problem, no doubt. But I can't find the source !

Any help would be very very much appreciated !!

Thanks,

---

