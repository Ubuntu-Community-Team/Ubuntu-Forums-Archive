---
title: "[Q] MTRR Uncachable"
date: 2013-07-20
forum: Hardware
---

### Post by Digital Prion on 2013-07-20
Thanks for reading.

I have a query regarding MTRR. I'm not sure I want to call it an issue yet. Note that my motherboard is an Asus P67 Sabertooth running the latest BIOS firmware as of this time. I have 16GB of RAM.

```

cat /proc/mtrr 
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  512MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg04: base=0x200000000 ( 8192MB), size= 8192MB, count=1: write-back
reg05: base=0x400000000 (16384MB), size=  512MB, count=1: write-back
reg06: base=0x41f000000 (16880MB), size=   16MB, count=1: uncachable

```

Note the uncachable line. This is something that I've encountered on both Xubuntu and Gentoo, with multiple different 3.x kernels, so it's likely hardware in origin. My research shows that this can be the cause of graphics problems, the least being a drop in framerate when using 3D applications.

Apparently enabling 'enable_mtrr_cleanup' in the kernel fixes the issue for many systems, but has had no effect for me. As an experiment, I did compile a kernel with this option DISABLED, and doing so made reg02 uncachable in lieu of reg06.

I'm curious if anyone more knowledgable here could offer me some insight. I question whether reg06 being unchachable is even an issue, since it cites '16880MB' range, where I don't even have that much RAM to begin with (16384MB is my maximum). But then, my ignorance about MTRR is starting to show. ;)

---

