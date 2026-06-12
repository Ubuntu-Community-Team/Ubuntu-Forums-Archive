---
title: "macbook intel video driver problem"
date: 2008-05-15
forum: Hardware
---

### Post by moaxey on 2008-05-15
i feel like my xorg.conf is a bit of a work of art these days...

particularly been loving my multi-screen setup for some time and not feeling like putting the old macbook back into mac at all.

since upgrading to hardy i cannot play video on the external monitor in my xinerama setup. Of course thats exactly where I want to play it (and used to play fine under gutsy)

I came accross this thread <https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b26796d178114bd3fdea5600480d8ab3137274d1> in relation to actually driving the external monitor at its native 1440x900 instead of the blocky 1280x800 it has been stuck on...

Can run it at that resolution, its satisfyingly crisp but the colour goes way off, it has a dark band down the left and moving windows in that area causes horizontal distortions...  the main laptop screen reverts to an unsightly 1024x768 although with fine colour.

the thread suggests using the newer intel driver instead of the current i810, and that should enable higher resolutions.

well the driver is installed, but when I spec it in the xorg.conf, i get this error:

```

(II) intel(0): Kernel reported 232960 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 931836 kB available
(WW) intel(0): Direct rendering is not supported when Xinerama is enabled
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f10420]
2: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7aadef3]
3: /usr/lib/xorg/modules/drivers//intel_drv.so(i830_allocate_2d_memory+0x13c) [$
4: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7aa89c8]
5: /usr/bin/X11/X(AddScreen+0x1fc) [0x8073d9c]
6: /usr/bin/X11/X(InitOutput+0x21e) [0x80a9c4e]
7: /usr/bin/X11/X(main+0x296) [0x8074526]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ca3450]
9: /usr/bin/X11/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

```

Can anyone help me?

---

