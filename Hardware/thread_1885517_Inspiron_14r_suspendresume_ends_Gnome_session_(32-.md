---
title: "Inspiron 14r suspend/resume ends Gnome session (32-bit)"
date: 2011-11-23
forum: Hardware
---

### Post by Hadogenes on 2011-11-23
I'm running 11.10 on a Dell Inspiron 14r, which has an Intel graphics controller that uses the i915 kernel driver.  I'm running into a number of issues related to suspending the display that are pretty strange.


[LIST=1]
[*]If I let the display turn off because of inactivity, it will usually refuse to come back to life.  When it does come back to life, it usually logs me out and sends me back to gdm.
[*]Suspend/resume does the same thing about 50% of the time.  If I close the lid and let the system suspend, when I open it again and resume, I've been sent back to gdm.
[/LIST]

I'm getting the impression that Xorg is crashing, but I'm having trouble figuring out where to look for meaningful logs and information.  Here's the graphics card information from 'lspci -vnn'.

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18) (prog-if 00 [VGA controller])
        Subsystem: Dell Device [1028:0456]
        Flags: bus master, fast devsel, latency 0, IRQ 41
        Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Capabilities: [a4] PCI Advanced Features
        Kernel driver in use: i915
        Kernel modules: i915
```

---

