---
title: "Non-Uniform Memory Access (NUMA)"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by masebase on 2007-08-09
I installed the 32-bit ubuntu 7.04 on a dual processor box what AMD opterons.  I then installed numactl and run

```
numactl --hardware
```

and got

```
libnuma: Warning: /sys not mounted or no numa system. Assuming one node: No such file or directory
available: 1 nodes (0-0)
libnuma: Warning: /sys not mounted or invalid. Assuming one node: No such file or directory
node 0 cpus:
node 0 size: <not available>
node 0 free: <not available>
libnuma: Warning: Cannot parse distance information in sysfs: No such file or directory
No distance information available.

```

So this make me think NUMA is not enable.  Does anyone know if you can start ubuntu with NUMA enabled and how?  I have a other computers running CentOS and it had NUMA enabled be default.

---

### Post by redsaz on 2007-08-09
I was able to install numactl on my 64-bit Ubuntu 7.04, running on an Athlon 64 x2 proc. Here's the result of running numactl --hardware:
```

$ numactl --hardware
available: 1 nodes (0-0)
node 0 cpus: 0 1
node 0 size: 2046 MB
node 0 free: 419 MB
node distances:
node   0 
  0:  10 


```

So it appears that NUMA is a go on my setup. Perhaps it is for 64-bit Ubuntu installs only?

---

