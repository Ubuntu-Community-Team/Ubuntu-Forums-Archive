---
title: "Temperature sensors"
date: 2011-01-21
forum: Hardware
---

### Post by perspectoff on 2011-01-21
Long ago, the Linux kernel ignored temperature sensors. In versions of (K)Ubuntu prior to Karmic, temperature sensor routines were not mandatory.

Then in Karmic there were lots of problems as the Linux kernel made temperature sensors mandatory. Later in Karmic some of those problems seemed to have been fixed and the temperature sensor routines made optional. 

Now, in Lucid and later, those temperature sensors are again mandatory and so the kernel refuses to boot on my old Intel motherboards/CPUs that do not have temperature sensors.

The workarounds I had to undertake to get Karmic working were extensive, and I eventually preferred just to leave Jaunty on those computers.

Does anyone know of an easy way to turn off the temperature sensor monitoring in recent Linux kernels?

---

