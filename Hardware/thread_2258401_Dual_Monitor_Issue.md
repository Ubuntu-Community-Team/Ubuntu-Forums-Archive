---
title: "Dual Monitor Issue"
date: 2014-12-27
forum: Hardware
---

### Post by adam111 on 2014-12-27
Hello I am new to this forum I hope I am posting this in a relevant area

I have been using Ubuntu for awhile and I have had no problem everything i have installed it on works out of the box.

I recently tried using duel monitors on Ubuntu and its gone wrong. It stopped me using my screens even when I tried using one 

They are different brand but both 19 inches and 1440x900 

When i try and run duel boot it either cycles through the resolution or just goes black. Sound still works sometimes it cycles back but 

Can anyone offer some advice i have read a bit into Xrandr and a few other things but scripting was mentioned and not my best topic. I think it mentioned scripting by setting default values and having it as a certain file but I'm confused any help would be great.


I stopped the cycling problem i believe by making them mirrored but not what I want

the mirroring seems to have fixed the cycling for my account at least

Im running a Acer veriton 1.7GB of video ram 3 GHZ intel core duo trying to duel monitor 2 1440x900 19 inch screens

---

### Post by QIII on 2014-12-27
Hello!

It would be very helpful if you would tell us what graphics adapter your machine uses.

Could you post the results of the following commands in the terminal?

```
lspci | grep VGA
```

and

```
sudo lshw -C video
```

---

### Post by adam111 on 2014-12-27
Thanks for the help

reponse first command
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


response to second command

  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:d0300000-d037ffff ioport:1800(size=8) memory:c0000000-cfffffff memory:d0400000-d043ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d0380000-d03fffff




Im currently using VGA i think if thats the one with the blue end and i am using DVI

---

