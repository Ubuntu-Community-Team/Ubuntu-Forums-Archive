---
title: "intel graphic not installed (vaio vgn-cs290)"
date: 2012-01-02
forum: Hardware
---

### Post by sinashahab on 2012-01-02
hi dear

i have installed ubuntu 11.04 and it had not get Acceptance my graphic card !

my graphic card's name is Intell Corporation Mobile 4 Series.

these are my devies information:
> 
root@SSh-Ubuntu:/home/robo# sudo lspci -v00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Sony Corporation Device 903f
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0a <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device 903f
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 60f0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Sony Corporation Device 903f
    Flags: bus master, fast devsel, latency 0
    Memory at 93400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 3
i have change grub to  GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.i915_enable_rc6=1"
but this is not work too.

excuse me for my bad english:D

---

### Post by sinashahab on 2012-01-02
who can solve my problem?;)

---

### Post by Mark Phelps on 2012-01-02
Unless you are stuck in the Command Line Interface, if you are able to get to a Desktop, then the graphics drivers ARE installed.

---

### Post by sinashahab on 2012-01-03
but i can't use the visual effects in ubuntu !
and my graphic not in additional drivers !

are you what know?

---

### Post by whatthefunk on 2012-01-03
> **sinashahab said:**
> but i can't use the visual effects in ubuntu !
and my graphic not in additional drivers !

are you what know?

This seems to be a recurring problem:
[http://ubuntuforums.org/showthread.php?t=1426632](http://ubuntuforums.org/showthread.php?t=1426632)

Some threads that might help you out:
[http://ubuntuforums.org/showthread.php?t=1132272](http://ubuntuforums.org/showthread.php?t=1132272)
[http://ubuntuforums.org/showthread.php?t=1333370](http://ubuntuforums.org/showthread.php?t=1333370)

Didnt find a very good solution for you though...

---

### Post by sinashahab on 2012-01-03
but i don't have visual effect in my system>per,,>app,,
my graphic card isn't in system>admin,,>addition drivers  too

:((

i wanna have visual effect:( i hope system can't exists my driver well:D

One help me . what do i do ??

---

