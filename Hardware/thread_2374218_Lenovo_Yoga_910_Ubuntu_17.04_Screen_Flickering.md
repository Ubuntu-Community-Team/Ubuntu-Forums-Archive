---
title: "Lenovo Yoga 910 Ubuntu 17.04 Screen Flickering"
date: 2017-10-13
forum: Hardware
---

### Post by abrahamlong on 2017-10-13
Hello guys my screen is flickering like crazy after 2 tries of set ups.

here is my -lshw -C video results
*-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:126 memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:3000(size=64) memory:c0000-dffff

My resolution is 3840x2160
Please help me getting crazy!

---

### Post by mörgæs on 2017-10-14
Hi, welcome to the fora.

The 910 is about as new as hardware can get. Does 17.10 give a better result?

---

### Post by abrahamlong on 2017-10-16
i didnt try the 17.10

---

### Post by mörgæs on 2017-10-17
It was meant as suggesting you to try it.

---

### Post by decemberpei on 2018-05-31
Also facing similar issue(Ubuntu 16.04 instead), solved by rolling back kernel. Now I'm on 4.10.0-041000-generic and the issue is gone. Hope this helps!

---

### Post by wildmanne39 on 2018-05-31
Hello and welcome to the forum decemberpei, please do not look up all threads and put the same answer in each one, that is considered crossposting.

Thanks

---

