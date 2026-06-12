---
title: "intel graphics screen ficker - Thinkpad T500"
date: 2010-06-18
forum: Hardware
---

### Post by HankB on 2010-06-18
Since upgrading to 10.04, I get occasional flickering on my laptop internal screen. This appears to be momentary garbling of the image toward the bottom of the screen. This is not a show stopper but is mildly annoying and if there is an easy solution, I'd like to apply it.

From Xorg.0.log

```
(--) PCI:*(0:0:2:0) 8086:2a42:17aa:20e4 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf4400000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
(--) PCI: (0:0:2:1) 8086:2a43:17aa:20e4 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf4200000/1048576
...
(II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
(--) intel(0): Chipset: "GM45"
```


from 'lspci -v'
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Lenovo Device 20e4
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at f4400000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [d0] Power Management version 3
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Lenovo Device 20e4
        Flags: bus master, fast devsel, latency 0
        Memory at f4200000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: [d0] Power Management version 3

```

Visual effects are turned off. Any pointers to where to look for a solution would be appreciated.

thanks,
hank

---

### Post by GeorgeOfTheBush on 2010-06-18
Check if this thread helps.

[http://ubuntuforums.org/showthread.php?t=1473580](http://ubuntuforums.org/showthread.php?t=1473580)


Another one:

[http://ubuntuforums.org/showpost.php?p=9142658&postcount=12](http://ubuntuforums.org/showpost.php?p=9142658&postcount=12)

---

### Post by HankB on 2010-06-18
Yes - thank you!

Modifying the line in /etc/default/grub to be:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.powersave=0"
```
from:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
seems to have solved the problem.

Oddly enough, adding /etc/modprobe.d/i915-disable-powersave.conf with
```
i915.powersave=0
```
did not seem to make a difference.

Many thanks,
hank

---

