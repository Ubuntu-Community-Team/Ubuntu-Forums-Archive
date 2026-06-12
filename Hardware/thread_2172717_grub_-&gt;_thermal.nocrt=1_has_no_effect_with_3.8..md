---
title: "grub -&gt; thermal.nocrt=1 has no effect with 3.8.0-29 kernel"
date: 2013-09-06
forum: Hardware
---

### Post by f3dja on 2013-09-06
Hi!

I've been using Ubuntu 12.04 for quite some time now; a long time ago I had trouble with funny temperature readings (i.e. constantly ~55°C, one single temperature reading between 120 and 230°C, immediately followed by 55°C again). Since I figured that something is wrong with my sensors, I disabled the "automatic shutdown" by adding "thermal.nocrt=1" to the default CMDLINE in /etc/defaults/grub.

Recently, I switched to the 3.8.0-29 kernel; the "thermal.nocrt=1" setting is still present, however now (with the new kernel) my laptop shuts down randomly:
thermal_sys: Critical temperature reached(224 C),shutting down
thermal_sys: Critical temperature reached(129 C),shutting down
I.e. the "thermal.nocrt=1" switch is not working any more.... 
Is this a bug or is it intentional?

Best wishes
Fedja

---

### Post by netvope2 on 2013-10-23
I had the same problem, but "thermal.off=1" fixed it for me.

---

