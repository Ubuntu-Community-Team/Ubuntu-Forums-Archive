---
title: "ASUS M5200N 87 degrees C+!  Is this normal?"
date: 2006-05-07
forum: Hardware &amp; Laptops
---

### Post by new2linux9 on 2006-05-07
Would another ASUS user mind confirming if the following is normal?

> marco@laptop:~$ acpi -V
     Battery 1: charged, 97%
     Thermal 1: active[0], 87.0 degrees C
  AC Adapter 1: on-line
marco@laptop:~$ acpi -V
     Battery 1: charged, 97%
     Thermal 1: active[0], 71.0 degrees C
  AC Adapter 1: on-line
marco@laptop:~$ acpi -V
     Thermal 1: active[0], 59.0 degrees C
  AC Adapter 1: on-line
marco@laptop:~$ acpi -V
     Thermal 1: active[0], 53.0 degrees C
  AC Adapter 1: on-line

I have already taken it back to ASUS and they changed the fan, as before sometimes it went to 93 degrees C plus!  However after reading some of the posts, some people say a laptop should be running between 50 - 60 degrees.  Does anyone else's laptop run this high.  Any ASUS users?

Specs: Intel Centrino 1.5GHZ, 512MB Ram, 60GB

 > *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: X1
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KB
             capacity: 32KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-cache
             size: 2MB
             capacity: 2MB
             capabilities: pipeline-burst internal varies unified

---

