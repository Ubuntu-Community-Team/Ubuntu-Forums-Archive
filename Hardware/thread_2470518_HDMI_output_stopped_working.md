---
title: "HDMI output stopped working"
date: 2022-01-02
forum: Hardware
---

### Post by JimLS on 2022-01-02
I have an Ubuntu 14.04 system I use with an HDMI TV.  It has a motherboard with VGA only so I have a video card for HDMI that also has vga and DVI connectors.

I wanted to check the latency of the system for LinuxCNC thinking I may switch this with another PC.  Booted a live CD of Ubuntu 10.04 with real time kernel and had some trouble with displays so connected VGA display to motherboard port.  Also connected it to video card VGA port and got that to work with HDMI disconnected.  Now when I reboot the PC into 14.04 on the hard drive the system works (I can get to it with ssh and also see the web page for Mythtv on another PC) but I don't have HDMI output which was the default display.  Not sure how anything changed but HDMI out does not work despite several reboots.

Card info:
```

sudo lshw -C video
  *-display
       description: VGA compatible controller
       product: GT218 [GeForce 8400 GS Rev. 3]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:44 memory:df000000-dfffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:ec00(size=128) memory:def80000-deffffff


```

---

### Post by JimLS on 2022-01-02
Doh!  I had a bad cable with an intermittent connection.  Works fine with a good cable.

---

