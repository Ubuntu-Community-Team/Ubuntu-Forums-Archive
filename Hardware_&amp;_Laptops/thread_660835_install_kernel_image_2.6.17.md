---
title: "install kernel image 2.6.17?"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by zhangweiwu on 2008-01-07
Dear all

I bought a hardware (EC321 wireless modem) that was reported to be working on Ubuntu 6.04. It doesn't work for me. I searched other forums where it says this hardware is no longer supported. The latest kernel that known to support this device is 2.6.17.

The support for this hardware is not intentionally dropped. I believe it's because the hardware is a Chinese product and the driver writer doesn't have one of it. I can offer him such a card if he likes to have one for testing.

anyway, to use it I need to roll back to the old kernel. I found it's no longer available by searching in aptitude. How can I find this old kernel and install it? And is it possible (to install old kernel on new Ubuntu 7.10) at all?

I tried to google the old kernel image .deb package but didn't find one for Ubuntu.

---

### Post by Jussi Kukkonen on 2008-01-07
> 
anyway, to use it I need to roll back to the old kernel. I found it's no longer available by searching in aptitude. How can I find this old kernel and install it? And is it possible (to install old kernel on new Ubuntu 7.10) at all?

Sure. You can look for the packages on packages.ubuntu.com, but I'd probably get the source and compile (since the packages aren't for your OS strictly speaking)...  see e.g. [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

It's up to you if you want to use kernel.org kernel sources or the some ubuntu kernel sources (which may have some good or bad patches).

---

