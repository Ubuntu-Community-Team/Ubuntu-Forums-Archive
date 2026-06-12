---
title: "Nvidia driver 1.0-9755 and ASUS F3Jv go7600 laptop"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by largecat on 2007-04-14
I am trying to get the Nvidia driver 1.0-9755 working on my ASUS F3Jv (go7600 gpu) laptop.

I have installed kernel 2.6.20-15, the corresponding restricted module package and nvidia-glx-new from the Feisty repository.

X moans that the Nvidia kernel module is version 1.0-9631 and the X module version is 1.0-9755.

If I manually remove the nvidia kernel module (with rmmod) and modprobe the correct one (nvidia_new.ko - 1.0-9755) then X happily starts up.

How is the kernel module selected?

I have noticed there is a file "/usr/share/linux-restricted-modules/2.6.20-15-generic/modules.alias.override/nvidia" which appears to give PCI parameters and the corresponding module type. Do I need to make an addition to this file for my card?

The lspci -v output for my card (if that helps) is:
```
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0398 (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1440
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at bc00 [size=128]
        [virtual] Expansion ROM at fbfe0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0
```

or numerically:
```
01:00.0 0300: 10de:0398 (rev a1)
        Subsystem: 1043:1440
```

Thanks for any help.

**EDIT:** Upgrading linux-restricted-modules-common and linux-restricted-modules-generic fixed the problem.

---

