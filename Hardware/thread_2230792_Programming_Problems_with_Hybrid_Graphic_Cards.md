---
title: "Programming Problems with Hybrid Graphic Cards"
date: 2014-06-21
forum: Hardware
---

### Post by thyagobr on 2014-06-21
Hi everyone,

So, I'm a developer, but I'm stumbling into a problem for some time now. My Dell Vostro laptop has hybrid graphic cards:

```
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0616
    Flags: bus master, fast devsel, latency 0, IRQ 62
    Memory at f1000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
(...)


09:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)
    Subsystem: Dell Device 0616
    Flags: bus master, fast devsel, latency 0, IRQ 65
    Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

```

The problem is that, whenever I try to run either SDL directly (through C++ code) or a pygame code (that, supposedly, uses SDL indirectly), I get:

```
Traceback (most recent call last):
  File "main.py", line 7, in <module>
    screen = pygame.display.set_mode((640, 360), 0, 32)
pygame.error: No available video device

```

I suppose the system is failing to pick one of the graphic cards, but that's just a wild guess. Would anyone have any advice for me?
Thanks =]

---

