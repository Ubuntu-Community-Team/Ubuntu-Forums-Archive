---
title: "Cheap AMD Graphics Card"
date: 2022-04-21
forum: Hardware
---

### Post by Quarkrad on 2022-04-21
I'm running 20.04 and having various issues with my Nvidia graphics card (have i5 9400 that does not support on board graphics).  Reading 'around' it looks like AMD/Radian is a good option but which one?  This is for a basic non gaming machine - occasionally looking at youtube videos.  I have sort of homed in on a fireGL V750 but I also keep reading things like 'get any old ATI graphics card'.  It would be nice to hear from fellow ubuntu 20.04 users who have a 'basic' Radeon graphics card that works - not being familiar with the ati range this is difficult.

---

### Post by Autodave on 2022-04-21
I only use nVidia and rarely have any issues.  What model card is yours?  Did you install any drivers for it and if so, where did you get the driver and what one did you install?

---

### Post by Quarkrad on 2022-04-21
Thanks Autodave.  It is my wife's machine.  The card is shown as:

```
liz@lizubuntu:~$ sudo lshw -C video
[sudo] password for liz: 
  *-display                 
       description: VGA compatible controller
       product: GK208B [GeForce GT 710]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:130 memory:4a000000-4affffff memory:40000000-47ffffff memory:48000000-49ffffff ioport:4000(size=128) memory:c0000-dffff

```

also

```
liz@lizubuntu:~$ lsmod | grep video
video                  53248  1 nouveau
```

The reason for posting is the machine is suddenly randomly crashing.  The last one filed up my syslog file with *nouveau 0000:01:00.0: fifo: SCHED_ERROR 20* pages and pages and pages!

GUI wise (Software Updates) the Additional Drivers section shows me using *X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau(open source)*

---

### Post by rsteinmetz70112 on 2022-04-21
Is there an Proprietary Nvidia Driver available for that card? I find that on some hardware the open source nouveau is glitchie. Nvidia has taken to discontinuing drivers for some older chip sets.

---

### Post by Autodave on 2022-04-21
That takes the old 340 driver.

---

### Post by TheFu on 2022-04-21
> **Autodave said:**
> That takes the old 340 driver.

Only if you are willing to use proprietary drivers.  Not everyone makes that choice.

---

### Post by Tadaen_Sylvermane on 2022-04-22
For amd anything using the amdgpu driver is a good bet if you end up changing it. I'm using an RX570 and it runs beautifully with the open source drivers. I'd argue better than on the Windows side of things.

---

### Post by Yellow Pasque on 2022-04-23
You might want to try booting in to an older kernel or installing the nvidia driver before concluding that there's a physical issue with the GPU.

Also, the i5-9400 supposedly has a built-in GPU: [https://www.intel.com/content/www/us/en/products/sku/134898/intel-core-i59400-processor-9m-cache-up-to-4-10-ghz/specifications.html](https://www.intel.com/content/www/us/en/products/sku/134898/intel-core-i59400-processor-9m-cache-up-to-4-10-ghz/specifications.html)
EDIT: It seems there's a i5-9400**F** variant without a GPU. Is that what you have?
EDIT2: What is a "FireGL V750"? I think you typo'd the model number.

> **Tadaen_Sylvermane said:**
> I'm using an RX570 and it runs beautifully with the open source drivers.

Yeah, I was thinking an RX550 would be a good candidate for OP if a new card is needed.

---

### Post by #&amp;thj^% on 2022-04-23
> **Autodave said:**
> That takes the old 340 driver.

Are you sure??
I have one running the 470. driver.
however that is totally up to the OP
```
Device-1: NVIDIA GK208B [GeForce GT 710] vendor: Micro-Star MSI 
  driver: nvidia v: 470.57.02 bus ID: 40:00.0 chip ID: 10de:128b
```

---

