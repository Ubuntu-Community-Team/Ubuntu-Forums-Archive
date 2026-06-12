---
title: "multiple video cards &amp; monitors"
date: 2016-01-03
forum: Hardware
---

### Post by idee on 2016-01-03
I have a clean  install of Lubuntu 15-10.  I would like to use both video cards across 3 monitors.  (2 on one, 1 on the other). It identifies both cards (see below), but seems to only be accessing a single monitor per card.  Each card can support 2 monitors, so in theory should be able to drive 4 monitors.   Any  help is appreciated.

Additional info. I installed Xubuntu first.  It did see and set up both    video cards and all three monitors fired up right away. I had some    issues with the mouse freezing that we couldn't resolve so I reformatted    and installed Lubuntu.  The mouse issues are gone with Lu, so all is    great here.  What is the difference between the two systems?   What  settings or commands can be altered to find the additional monitor?   Does anyone have experience with the X.Org Nouveau driver verses the  NVIDIA driver?  Would that make a difference?

```
lubuntu@lubuntu:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: G86 [Quadro NVS 290]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:32 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:3100(size=128)
  *-display
       description: VGA compatible controller
       product: GT216 [GeForce GT 220]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:20:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:33 memory:f2000000-f2ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:1100(size=128) memory:f3080000-f30fffff
```

thanks for the help if anyone can chime in here.

---

### Post by idee on 2016-01-04
anyone?

---

### Post by James_Creasy on 2016-01-05
I've had some problems getting monitors to work right, some symptoms documented here: [http://ubuntuforums.org/showthread.php?t=2257192](http://ubuntuforums.org/showthread.php?t=2257192)

---

### Post by idee on 2016-01-05
> **James_Creasy said:**
> I've had some problems getting monitors to work right, some symptoms documented here: [http://ubuntuforums.org/showthread.php?t=2257192](http://ubuntuforums.org/showthread.php?t=2257192)

Thanks  This seems to be a pretty quiet forum.  

From reading, it looks like the best option may be to install the Nvidia driver as opposed to the Nouveau.  If I do that and it hangs the system, how do I switch it back?  Is there a safe mode that will allow me to change it back?

---

