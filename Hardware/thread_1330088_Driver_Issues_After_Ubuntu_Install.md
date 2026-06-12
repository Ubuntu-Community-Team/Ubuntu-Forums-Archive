---
title: "Driver Issues After Ubuntu Install"
date: 2009-11-18
forum: Hardware
---

### Post by dilip123 on 2009-11-18
i just installed the latest version of ubuntu as a sual boot with vista. when i go to the hardware drivers window, it says there is not hardware it recognizes. The touch pad works fine but the wireless adapter doesnt work and i dont have internet. 
my laptop is a dell xps m1210, does anyone know what could solve these issues?
thanks

---

### Post by dilip123 on 2009-11-18
bump.
ethernet does work, its just wireless thats not at all working.

---

### Post by Yellow Pasque on 2009-11-18
What wireless adapter do you have and what driver is in use?
```
sudo lshw -C network
```

---

### Post by dilip123 on 2009-11-18
it gives me this for my wirelss card:
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:ecffc000-ecffffff memory:e0000000-e00fffff(prefetchable)

its a broadcom 440x 10/100 integrated controller (from dell).
thanks

---

### Post by dilip123 on 2009-11-19
somehow it found the drivers after a couple restarts. thanks

---

