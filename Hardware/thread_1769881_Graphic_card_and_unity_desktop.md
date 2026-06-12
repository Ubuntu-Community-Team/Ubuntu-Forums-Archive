---
title: "Graphic card and unity desktop???"
date: 2011-05-28
forum: Hardware
---

### Post by hieusun2011 on 2011-05-28
I just don't know how to name this thread to describe this problem.
I have a laptop dell vostro 3550 (2 graphic card: Intel HD 3000 and ATI HD 6630) on which I installed ubuntu 11.04 (32bits) and i can use unity desktop environment on the first boot.

When the Additional Drivers told me to activate ATI drivers, I click on activate and after that restarted the laptop. When ubuntu boot up, it said that:"you do not have the hardware required to run Unity"

I opened System->Preferences->ATI Catalyst Control Center
An error occured: 
```
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
```

But after i removed ATI driver, it turned back to unity desktop. Unfortunately, the search bar is so lag when I type words

Needs help T.T I want to install my graphic card properly and also make unity desktop work
Thanks
Sr for my English

---

### Post by sikander3786 on 2011-05-28
Welcome to the forums :)

From Unity, press the <Super> (Windows Logo Button) and type, 'Terminal'. Open it and post the output of this command:

```
lshw -c video
```

It would tell us about your graphics card/drivers currently is use.

---

### Post by hieusun2011 on 2011-05-29
Here =) ( I'm running terminal in gnome desktop )
```
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: NI Whistler [AMD Radeon HD 6600M Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:e0000000-efffffff memory:f7b20000-f7b3ffff ioport:e000(size=256) memory:f7b00000-f7b1ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

---

