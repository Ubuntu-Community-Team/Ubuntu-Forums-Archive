---
title: "Intel HD 4000 (Ivy Bridge) graphics on Ubuntu 10.04 LTS 64bit"
date: 2012-07-24
forum: Hardware
---

### Post by galapogos on 2012-07-24
Hi,

I'm have a Intel Core i7-3700 system with Intel HD 4000 graphics on an Asus H77 motherboard. I have 2 monitors, a 19" 1280x1024 LCD connected via VGA, and a 23" 1920x1080 LCD connected via DVI. I've installed Ubuntu 10.04 LTS 64bit.

I'm having trouble with the intel display driver. It's not detecting my display hardware, and hence I'm not getting proper dual monitor setup (my desktop is mirrored rather than extended), nor am I getting proper resolution (my max resolution is 1280x1024).

I've tried installing the glasen drivers using the following commands:

```

sudo add-apt-repository ppa:glasen/intel-driver sudo apt-get update sudo apt-get upgrade sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty

```However, that didn't change anything. On a previous Core i5-2400 system (Sandy Bridge with Intel HD 3000 graphics), installing the glasen drivers worked.

My lspci output for the processor and display is as follows:

```

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCIe advanced features <?>

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCIe advanced features <?>

```My xrandr -q output is as follows:
```

Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  

```My lshw -C video output is as follows:
```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

lsmod shows no drivers being assigned to video.

Does anyone know how to get the correct drivers properly installed on this system?

I would be happy to provide anymore information if required.

I need to be working on 10.04 LTS 64bit, so it is not possible for me to update to a newer OS version at this time.

Thank you.

---

### Post by bissong on 2012-10-22
Hi galapogos,

I'd like to know if you found a solution for this issue as I'm facing the same one. I'm under Ubuntu 11.04 on my DELL N5520 with a kernel 3.4 but my second display is always a clone of the first one :(

Thanks!

---

