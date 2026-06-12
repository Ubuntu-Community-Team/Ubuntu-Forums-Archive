---
title: "Intel915 Improvements ?"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by iLoVe.cF- on 2007-04-12
Hi...

how did you give the intel915 more memory again ?

```
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 16064 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) I810(0): Chipset: "915GM"
(--) I810(0): Linear framebuffer at 0xD0000000
(--) I810(0): IO registers at addr 0xFEB80000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 16124 kB stolen memory.
(II) I810(0): Kernel reported 236800 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 947196 kB available
(II) I810(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) I810(0): Monitoring connected displays enabled
(--) I810(0): Pre-allocated VideoRAM: 16124 kByte
(==) I810(0): VideoRAM: 65536 kByte
```

I wanna give it 128 mb as standard all the time

---

### Post by zgornel on 2007-04-12
Just add in /etc/X11/xorg.conf in "Section Device" : *VideoRam 131072* It provides the maximum shared memory available.

---

### Post by iLoVe.cF- on 2007-04-12
thanks alot.. that improved actually my font.. dont know how.. but it did.. 
and my performance my some fps.. beryl got an little improvement..

50fps in glxgears with beryl 300 without.. and that made my cube run smooth enough so i can use it without getting mad cuz of the low fps.

i wont call it lagg.. lagg means Delay delay isnt what it is. :p learn it folks.. 
Low fps isnt LAGG

---

