---
title: "Nvidia GTX 1650 2 Identical Cards Getting an error Unclaimed"
date: 2024-02-06
forum: Hardware
---

### Post by itoxactai on 2024-02-06
[COLOR=#424242][FONT=arial]We are trying to configure Nvidia GTX 1650 2 Identical Cards[/FONT][/COLOR]


[U]System Configuration:

[/U]CPU: Asus-i9 
Motherboard :Asrock  ([B560M Pro4]("https://www.asrock.com/model.asp?m=B560M%20Pro4"))
Gpu's: Nvidia-GTX-1650 (2 cards)
Operating system: Ubuntu-22.04


[COLOR=#424242][FONT=arial]So while working with windows 10 operating system,it showing 2 cards and working fine.But in Ubuntu-22.04.it shows 1 of the card as unclaimed and not working.Please find the below output[/FONT][/COLOR]




[COLOR=#424242][FONT=arial]@ASUS-i9-GTX-GTX:~$ sudo lshw -C display[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]*-display[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]description: VGA compatible controller[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]product: TU116 [GeForce GTX 1650][/FONT][/COLOR]
[COLOR=#424242][FONT=arial]vendor: NVIDIA Corporation[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]physical id: 0[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]bus info: pci@0000:01:00.0[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]version: a1[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]width: 64 bits[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]clock: 33MHz[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]capabilities: pm msi pciexpress vga_controller bus_master cap_list rom[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]configuration: driver=nvidia latency=0[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]resources: irq:153 memory:71000000-71ffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:3000(size=128) memory:72000000-7207ffff[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]*-display[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]description: VGA compatible controller[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]product: RocketLake-S GT1 [UHD Graphics 750][/FONT][/COLOR]
[COLOR=#424242][FONT=arial]vendor: Intel Corporation[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]physical id: 2[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]bus info: pci@0000:00:02.0[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]logical name: /dev/fb0[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]version: 04[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]width: 64 bits[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]clock: 33MHz[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]configuration: depth=32 driver=i915 latency=0 mode=1920x1080 resolution=1920,1080 visual=truecolor xres=1920 yres=1080[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]resources: iomemory:600-5ff iomemory:400-3ff irq:152 memory:6013000000-6013ffffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff[/FONT][/COLOR]

[COLOR=#424242][FONT=arial]*-display UNCLAIMED[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]description: VGA compatible controller[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]product: TU116 [GeForce GTX 1650][/FONT][/COLOR]
[COLOR=#424242][FONT=arial]vendor: NVIDIA Corporation[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]physical id: 0[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]version: a1[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]width: 64 bits[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]clock: 33MHz[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]capabilities: pm msi pciexpress vga_controller cap_list[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]configuration: latency=0[/FONT][/COLOR]
[COLOR=#424242][FONT=arial]resources: iomemory:600-5ff iomemory:600-5ff memory:6000000000-600fffffff memory:6010000000-6011ffffff ioport:5000(size=128) memory:72280000-722fffff



[/FONT][/COLOR]

---

### Post by MAFoElffen on 2024-02-07
Log into your User using Xorg and post the 'xorg.0.conf' log please, [COLOR=#b22222]posted within Code Tags[/COLOR].

Not in the clear, like you did with the last post. Press "Adanced Reply" > Thne use the "#" icon fomr the Extended Tool Menu to insert Code Tags. > Then paste the contents between them.

---

