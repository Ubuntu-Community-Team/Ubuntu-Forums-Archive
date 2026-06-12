---
title: "No Direct Rendering/DRI with intel 965GM"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by smylie on 2007-05-26
I'm trying to get direct rendering going using my intel 965GM video card with kernel 2.6.21.3 (custom kernel as the standard feisty kernel doesn't create a /dev/agpgart).
X works, but I can't get direct rendering to enable. 

The relevant section of the Xorg.log states:

```
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI

.
.
.(II) intel(0): Kernel reported 364032 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1456124 kB available
(**) intel(0): VideoRam: 128000 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
               large DRI memory manager reservation:
(II) intel(0): Allocating 6206 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1728 -> 1792).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00040000-0x03628fff: front buffer (55204 kB)
(II) intel(0): 0x0077f000:            end of stolen memory
(II) intel(0): 0x03629000-0x03638fff: xaa scratch (64 kB)
(II) intel(0): 0x03639000-0x041b4fff: back buffer (11760 kB)
(II) intel(0): 0x041b5000-0x04d30fff: depth buffer (11760 kB)
(II) intel(0): 0x04d31000-0x06d30fff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
.
.
. same repeated for card0-card14
.
.
.
(II) intel(0): [drm] drmOpen failed
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xd0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
```

Looking in /dev, i have a /dev/dri directory, but there's no contents - it's completely empty. 

Any one have any ideas as to why these entries could be missing? (Assuming that's why I can't get direct rendering enabled)

Cheers
Dave Smylie

---

### Post by smylie on 2007-05-29
Again - like most things, this was eventually fixed by upgrading to the latest version of the intel drivers (from git repository on freedesktop.org).

As soon as  I'd done that, I had a /dev/dri/card0 and dri was enabled =)

---

