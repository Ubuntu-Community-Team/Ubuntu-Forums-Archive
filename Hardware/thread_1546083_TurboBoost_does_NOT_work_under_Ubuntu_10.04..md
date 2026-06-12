---
title: "TurboBoost does NOT work under Ubuntu 10.04."
date: 2010-08-04
forum: Hardware
---

### Post by jdiezlopez on 2010-08-04
Hello, I've recently bought an HP Pavilion dv6 3040ES laptop with an i7 processor with Intel's TurboBoost technology so it can reach 2.8GHz under heavy load.

This works fine with Windows. I've run a benchmark called "linpack" from Intel, which is meant to measure the GFLOPs the processor is able to achieve, and it should bring TurboBoost on so it runs faster.

To my deception, none of this happens. I've been watching the processor's speeds with an utility called "i7z". It says TurboBoost should be enabled, but the truth is it isn't working. 

uname -a reports:

```
jdiez@jdiez-hp:~$ uname -a
Linux jdiez-hp 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

```I'm performing a full system update, and I'll try disabling acpi in the boot menu, although this is hacky.

Will keep this post updated when I finish the update, but any help would be greatly appreciated.

BTW, my processor is an i7 720QM. Really neat.

---

### Post by cascade9 on 2010-08-05
IIRC, the later kernels (2.6.33 or 2.6.34, I forget which) support turboboost.

That could be mainline kernels, not ubuntu kernels. You might want to have a look at this- 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036)

---

### Post by PresenceofMind on 2010-08-05
> **jdiezlopez said:**
> Hello, I've recently bought an HP Pavilion dv6 3040ES laptop with an i7 processor with Intel's TurboBoost technology so it can reach 2.8GHz under heavy load.

This works fine with Windows. I've run a benchmark called "linpack" from Intel, which is meant to measure the GFLOPs the processor is able to achieve, and it should bring TurboBoost on so it runs faster.

To my deception, none of this happens. I've been watching the processor's speeds with an utility called "i7z". It says TurboBoost should be enabled, but the truth is it isn't working. 

uname -a reports:

```
jdiez@jdiez-hp:~$ uname -a
Linux jdiez-hp 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

```I'm performing a full system update, and I'll try disabling acpi in the boot menu, although this is hacky.

Will keep this post updated when I finish the update, but any help would be greatly appreciated.

BTW, my processor is an i7 720QM. Really neat.

Update your kernel.

---

