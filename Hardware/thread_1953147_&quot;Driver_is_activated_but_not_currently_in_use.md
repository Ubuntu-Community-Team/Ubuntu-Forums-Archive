---
title: "&quot;Driver is activated but not currently in use&quot; I think I have two drivers activated"
date: 2012-04-05
forum: Hardware
---

### Post by ubunbu on 2012-04-05
I used additional drivers to install my NVIDIA driver but on reboot it goes to "fall back mode" where I get Gnome 2 for instance, instead of seeing Gnome 3, even though Gnome 3 is selected.

Through Additional Drivers I see the error in the subject 'activated but not currently in use'

This is the output of 

```
sudo lshw -c display
```

 >  *-display               
       description: VGA compatible controller
       product: GF108 [GeForce GT 555M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f0000000-f1ffffff memory:c0000000-cfffffff memory:d0000000-d3ffffff ioport:4000(size=128) memory:f2000000-f207ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:51 memory:f2400000-f27fffff memory:e0000000-efffffff ioport:5000(size=64)

As you can see it says vendor : nvidia and another vendor: intel

What do I do?

---

### Post by mikewhatever on 2012-04-05
You should read up on Nvidia's Optimus technology.

[http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus](http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus)

---

