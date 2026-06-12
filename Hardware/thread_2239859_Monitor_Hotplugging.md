---
title: "Monitor Hotplugging"
date: 2014-08-16
forum: Hardware
---

### Post by raghav5 on 2014-08-16
Hello, I am running Ubuntu 14.04 on a Lenovo x230 laptop. Not sure if this question fits better under hardware or desktop environments but...

At home I prefer to have the laptop docked with two external monitors connected and the internal screen off with the lid down. A recent problem is that if I undock the machine while it is in sleep/suspended state, when I open the screen I get a black screen. On one occasion I was able to enter my password and hit return, which brought the screen back to life but I have not been able to replicate this behaviour. Switching to another TTY (CTRL+ALT+F1) also does nothing. 

Should Unity be able to do this? I've used other DEs that do handle monitor configurations changing while suspended so I know it is possible..

---

### Post by raghav5 on 2014-08-16
Forgot to add... the graphics card is an Intel integrated. From lshw:

```
  *-display             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64)
```

---

