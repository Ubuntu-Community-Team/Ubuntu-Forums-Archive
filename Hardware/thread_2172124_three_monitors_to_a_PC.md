---
title: "three monitors to a PC"
date: 2013-09-03
forum: Hardware
---

### Post by ghitax on 2013-09-03
Hello
I installed Ubuntu 13:04 x64
on a motherboard Gigabyte Z68XP-ud3
This card has an HDMI On Board
I added a Nvidia GT240 with 3 video outputs


With Windows 8 I have installed and tested (and it works)
a 24-inch Monitor DVI (DVI output card Nvidia)
a 19-inch VGA monitor (VGA Card Nvidia)
a TV monitor (HDMI Output OnBoard motherboard)


works in Windows 8
Ubuntu does not allow me to use at the same time the Nvidia card and the HDMI output of the Motherboard.
That allows me to choose whether to use the output from BIOS or Nvidia On Board


if I connect all three monitors to the outputs of Nvidia PCI card allows me to use only two exits out of three.


You have no idea how can you do?

```

sudo lshw -c display 
  *-display               
       description: VGA compatible controller
       product: GT215 [GeForce GT 240]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f9000000-f9ffffff memory:d0000000-dfffffff memory:ee000000-efffffff ioport:bf00(size=128) memory:e0000000-e007ffff
  *-display UNCLAIMED
       description: Display controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm cap_list
       configuration: latency=0
       resources: memory:fb400000-fb7fffff memory:c0000000-cfffffff ioport:ff00(size=64)

```

and also

```

# lspci -x | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GT215 [GeForce GT 240] (rev a2)



```

---

### Post by prokher on 2013-11-21
I have the same issue (

When I set up nvidia card as primary adapter, I wee all three monitors in displays settings, but only of is enabled. If I enable others then system crashes completely. If I set embedded video card as a primary adapter then I simply do not see a display connected to nvidia card.

---

### Post by jp734 on 2013-11-21
Your video card doesn't have a displayport to be able to use three monitors with one card. So you will only be able to use two. The way around that I can think of is to create an xorg.conf file so you can manually setup your system to used two cards. Set the onboard as your primary monitor and the NVidia card for the other two.

---

### Post by Mark Phelps on 2013-11-21
> Your video card doesn't have a displayport to be able to use three monitors with one card.

That's not the OP's issue -- they are only using TWO monitors with their nvidia card.  The third monitor is connected to the motherboard.

---

