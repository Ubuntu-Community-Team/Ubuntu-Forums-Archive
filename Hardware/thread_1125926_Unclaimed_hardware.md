---
title: "Unclaimed hardware"
date: 2009-04-14
forum: Hardware
---

### Post by Ganek on 2009-04-14
Reviewing lshw's results found this:

*-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0

Can anyone tell what it is and how to get it's appropiate drivers?

Thanks.

---

### Post by jbrown96 on 2009-04-15
> **Ganek said:**
> Reviewing lshw's results found this:

*-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0

Can anyone tell what it is and how to get it's appropiate drivers?

Thanks.
This looks like your SouthBridge. It controls your memory and other bus devices. There's nothing you need to do to use it. If it wasn't working, you wouldn't be able to use Ubunty at all

---

### Post by Ganek on 2009-04-15
Great, j.

Thanks!

---

