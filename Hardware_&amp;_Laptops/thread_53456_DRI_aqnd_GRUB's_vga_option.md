---
title: "DRI aqnd GRUB's vga option"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by NeoChaosX on 2005-07-31
Okay, been trying out Splashy/UPower according to [this thread](http://www.ubuntuforums.org/showthread.php?t=41709), and it's been working fine up until now. Recently, I decided to recompile my DRI drivers for my Mobility Radeon 7500. THe drivers and modules installed properly, however when I rebooted, I found that my 3D performance had actually decreased (>200 fps in glxgears) ! I found it would go back to normal when I would remove "vga=" (kicks up the resolution of text mode, which is needed for UPower to work) from the Grub options.

So, does anyone else have this problem? Is there a way I can fix this so I can add "vga=" to my boot options and still get decent 3D performance? Or am I screwed?

---

### Post by Goshawk on 2005-08-06
Upower works with any framebuffer.
Try to set up he nvidia framebuffer to have best 3d accelleration plus a good bootsplash.

---

