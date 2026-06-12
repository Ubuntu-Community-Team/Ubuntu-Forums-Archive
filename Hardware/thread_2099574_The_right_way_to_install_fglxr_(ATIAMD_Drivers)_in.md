---
title: "The right way to install fglxr (ATI/AMD Drivers) in 12.10?"
date: 2012-12-29
forum: Hardware
---

### Post by Skyxer on 2012-12-29
I've recently and after testing several distros moved back to Ubuntu (I loved Debian, but Ubuntu felt more complete).

So the problem here is that I currently own an HP laptop (3315ep) with an ATI graphics card (5550m), which is available as a high performance card, paired with the included Intel card and it should be able to switch between them if (Switchable Graphics within the CCC).

**How do I install my graphics card and the available Catalyst Control Centre in a fresh 12.10 install?**

From what I've read there are some compatibility issues with X, kernel, Unity and the stable version of ATI drivers (hence the beta drivers availability), but since the posts are about 1 to 2 months old I do not know if that is the correct method any more (the related kernels in such threads are not the most recent). I've tried such methods, but **after installing both the stable and the beta drivers from the ATI website, Unity breaks after logging in**, and no window manager seems to work either, neither does fglxrinfo return any valid information.

Thank you for your time.

---

### Post by 2F4U on 2012-12-30
You may have already found this thread

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

Here the poster says it is working, but only under many prerequisites. It is best to verify the requirements before you start to follow the thread. Another point to note is that this method has been tested under 12.04, and what I read in the forum is that a lot of problems exist when using 12.10.

---

