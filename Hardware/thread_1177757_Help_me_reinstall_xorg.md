---
title: "Help me reinstall xorg"
date: 2009-06-03
forum: Hardware
---

### Post by charrah on 2009-06-03
I tried to install nVidia's beta 185 driver, and package nvidia-glx-185 seemed to conflict with something in xorg; since I installed using the hardware drivers dialog, I wasn't informed about this and rebooted me to a terminal. I had troubles removing the package or installing xorg so I booted the livecd and chroot'd in so I could copy and paste the error message:
```
Removing nvidia-glx-185 ...
dpkg-divert: error checking `/usr/lib/xorg/modules/extensions/libGLcore.so': No such file or directory
dpkg: error processing nvidia-glx-185 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx-185
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
So, what should I do to get that package removed and xorg back?

Edit:
I'm running Ubuntu 9.04 on AMD64

SOLVED:
I was able to uninstall nvidia-glx-185 by extracting a file called libGLcore.so from the .deb for nvidia-glx-185 to the path it expected and trying to uninstall it. Then I installed ubuntu-desktop everything worked once more.

---

