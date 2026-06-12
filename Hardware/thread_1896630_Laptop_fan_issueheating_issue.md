---
title: "Laptop fan issue/heating issue"
date: 2011-12-17
forum: Hardware
---

### Post by psudheera on 2011-12-17
hello friends. I got a problem which really bothering me. Please help me out.

I used to use Windows Seven, but recently I moved into Ubuntu which is really good. But the thing is my laptop getting too hot quickly and switch off suddenly like when we remove the battery. Then for a while I can't restart it. With Windows I never had this issue except when playing video games with high graphics. Even then I played like half an hour before it gets down. I install lm-sensors and here what it gives. Please friends I don't know what to do. If you want more information please ask. thank you

[IMG]http://dl.dropbox.com/u/25500756/Screenshot%20at%202011-12-17%2021%3A25%3A06.png[/IMG]

my laptop : Dell inspiron 5010

---

### Post by 2F4U on 2011-12-17
What are the hardware specs and what is the graphics card? What graphics driver do you use?

---

### Post by psudheera on 2011-12-17
> **2F4U said:**
> What are the hardware specs and what is the graphics card? What graphics driver do you use?

ATI-radeon 1 GB that's all I know.. Where Can I get more information.?

---

### Post by psudheera on 2011-12-17
> **psudheera said:**
> ATI-radeon 1 GB that's all I know.. Where Can I get more information.?
ok I got it.

description: VGA compatible controller
                product: Madison [AMD Radeon HD 5000M Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:47 memory:c0000000-cfffffff memory:fbe20000-fbe3ffff ioport:e000(size=256) memory:fbe00000-fbe1ffff


cpu
          description: CPU
          product: Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 4

memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 4GiB

multimedia
                description: Audio device
                product: Redwood HDMI Audio [Radeon HD 5600 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz

---

### Post by psudheera on 2011-12-18
bump

---

### Post by 2F4U on 2011-12-18
Did you try to install the proprietary ATI drivers, for example through the Additional Drivers utility? Are there processes running in the background that place a high burden on the CPU? You can find such processes by using top or htop.

---

### Post by psudheera on 2011-12-18
> **2F4U said:**
> Did you try to install the proprietary ATI drivers, for example through the Additional Drivers utility? Are there processes running in the background that place a high burden on the CPU? You can find such processes by using top or htop.

nope I didn't try it. can you explain exactly what should I do..?

---

