---
title: "Unknown Graphics Driver in Dell Inspiron 1545"
date: 2012-11-15
forum: Hardware
---

### Post by meijin3 on 2012-11-15
I've started playing games on my laptop and have noticed that my performance is far from desired. I went into "About This Computer" and clicked on the Graphics tab. It says that the driver is unknown and the experience is standard. In terminal I was able to find out the following info:

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 02aa
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at f6c00000 (64-bit, non-prefetchable) [size=4M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at efe8 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

I noticed that it says "Access Denied." Is there anything that I can do to fix this and if so, should I be seeing a major boost in performance? Thanks, forum contributors!

---

### Post by ahallubuntu on 2012-11-15
> **meijin3 said:**
> I've started playing games on my laptop and have noticed that my performance is far from desired. I went into "About This Computer" and clicked on the Graphics tab. It says that the driver is unknown and the experience is standard. In terminal I was able to find out the following info:

I noticed that it says "Access Denied." Is there anything that I can do to fix this and if so, should I be seeing a major boost in performance? Thanks, forum contributors!

I use Ubuntu 10.04 LTS on my 1545.  I don't recall if this model had an option for a discrete graphics card or not, but mine uses integrated graphics for sure, perhaps yours does too.  I don't play games on mine and the performance has been excellent for what I need.

I did an lshw on mine and I find that I have two displays: one for the LCD screen and one for the VGA connector:

```
sudo lshw -C display
[sudo] password for user: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:f6c00000-f6ffffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff
```

Could be you are seeing the same thing: just display 1 not plugged in.  But I am not using 12.04 (and you?).

In any case, I doubt you can do much to improve graphics performance on this laptop.  Integrated graphics, if that's what you have like I do, will be slow, and this was a budget laptop to start with.

You could upgrade the CPU - that could help.  I upgraded mine (was a Pentium Dual Core) to a Core 2 Duo P8700 2.5GHZ.  It's very easy to do on a 1545; the CPU compartment is accessible from the bottom.  But it may not be cost effective at this point, and I can't promise you it will double graphics performance or anything.  If by chance you have a Celeron CPU, though, I would upgrade it for sure.

---

### Post by meijin3 on 2012-11-15
This is what I just got:

```
sudo lshw -C display
[sudo] password for user: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff
```

Are there any drivers I can install so the system recognizes everything?

---

### Post by ahallubuntu on 2012-11-15
Have you tried plugging in an external monitor?  Then that other display driver should kick in.  If you don't need an external monitor, don't worry about it.  It's not going to change your LCD screen's performance at all.

---

### Post by meijin3 on 2012-11-15
> **ahallubuntu said:**
> Have you tried plugging in an external monitor?  Then that other display driver should kick in.  If you don't need an external monitor, don't worry about it.  It's not going to change your LCD screen's performance at all.

Oh, so you're saying that this will not have an effect on game performance?

---

### Post by BertN45 on 2012-11-15
If your gaming performance is stuck on your video, you are out of luck for the moment. Integrated video is not very good for gaming and probably there are no other drivers. Also switching to another distro will not help, because they are all using the same Linux kernel and same driver.

The gaming industry has detected Linux and there are some co-operations between hardware supplier and game suppliers to improve gaming performance. See:

[http://www.phoronix.com/scan.php?page=article&item=intel_sandy_threesome&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_sandy_threesome&num=1)

Hopefully your and mine Intel integrated video also profits from these initiatives. What might help is switching to Ubuntu 12.10 or if you have space for a double boot try the development release 13.04, which runs at Linux 3.7. It relatively nice now,but it might crash on one of the next updates.

---

