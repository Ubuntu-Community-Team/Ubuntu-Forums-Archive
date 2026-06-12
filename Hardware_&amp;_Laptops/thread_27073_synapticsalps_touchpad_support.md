---
title: "synaptics/alps touchpad support?"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by maxlock on 2005-04-14
Hi Folks,

 I've just performed a fresh install of Hoary on my HP zv5000. This unit has a synaptics/alps touchpad which isn't functioning under Ubuntu. 

 I'm a fairly experienced Debianite, and have it working under debian testing on the same machine. However, I've patched the kernel etc on that install.

  I read a forum message stating that the ALPs/synaptics patches would be rolled into the ubuntu kernels as of the Hoary relase. So what's the official line? do I need to grab the kernel source and patch it myself? Where's the archive for the kernel source, I can't find it in my apt cache?

 -Cheers Max.

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=maxlock] Where's the archive for the kernel source, I can't find it in my apt cache?

 -Cheers Max.[/QUOTE]


You have to install the kernel source package.

---

### Post by mendicant on 2005-04-15
Search for linux-source.  I have an alps touchpad and I still had to patch the kernel sources to get everything working correctly (using the alps.patch.gz in /usr/share/doc/xorg-driver-synaptics)--like the scroll by using the edge of the touchpad, disabling tap to click, that kind of thing.

---

