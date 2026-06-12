---
title: "nVidia GPU not detected after reboot."
date: 2019-09-29
forum: Hardware
---

### Post by poloniumq on 2019-09-29
Hello

A few days ago I noticed that instead of my dedicated GPU (nVidia GeForce GTX 1080 Ti), Intel integrated graphics was in use. I didn't think much of it and ran 
```
nvidia-settings
``` to change the GPU, but instead, I got 
```
ERROR: Unable to load info from any available system
```
Strange, I thought, and ran some other commands:
```
lspci | grep -i vga
```
Output:
```
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 630 (rev 04)
```



```
lshw -C video
```
Output:
```
  *-display                      description: VGA compatible controller
       product: HD Graphics 630
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:133 memory:f6000000-f6ffffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

I checked Aditional Drivers in Software and updates, no additional drivers available.

After this I went into BIOS and found that the main GPU was set to "Integrated", instead of "PCIE".
I thought about switching these settings, and I know that this might sound stupid, but decided not to, because I was afraid that I might lose the display entirely.
I want know if it is safe to change these settings (better safe than sorry), or if there is an other way to fix this.

Some other specs:
CPU: Intel® Core™ i7-7700
32GB RAM

---

### Post by Autodave on 2019-09-29
Assuming that your Nvidia card is in a PCIE slot and you have your monitor hooked up to the Nvidia card, then the BIOS should be changed.  What bothers me though, is how did it get changed to integrated?  That doesn't make any sense.

What Nvidia driver are you using and where did you get it from?

---

### Post by CatKiller on 2019-09-29
Check your connections, including power. If the hardware is connected and able to be powered it would show up in lshw, even if driver configuration meant that it wasn't actually being used.

---

### Post by poloniumq on 2019-09-30
I am using nvidia-390 and I got then from nvidias official site. My monitor has always been connected to the motherboard. I tried connecting it to the gpu but I got no image.

I have a theory that there might be a problem with the connection, so the gpu got switched

---

### Post by poloniumq on 2019-09-30
Could dust be interfering with the connection?

---

