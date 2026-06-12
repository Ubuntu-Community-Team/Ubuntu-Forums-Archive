---
title: "Do some distros have better hardware supporT?"
date: 2008-11-04
forum: Hardware
---

### Post by frito on 2008-11-04
Do some distos have better hardware support (i.e. Kubuntu vs Ubuntu) or is this more of a Parent linux thing (i.e. all debian based distros are the same), or is hardware support fairly uniform throughout linux?

Thanks

---

### Post by nixscripter on 2008-11-04
There are three levels of hardware support, when it comes to drivers:

1. Drivers in the mainline kernel. Almost every distro supports them, even if they don't ship them precompiled. These are usually pretty good.
2. Driver that distros or packages provide, but haven't made it into the mainline source yet. These are probably good, but are less reliable than those in the mainline kernel. If the distro decided to include them, they probably will support them.
3. Drivers that 3rd parties maintain. Some are good, some are bad, don't count on them.

99% of the drivers most of us desktop end-users use are category 1. Wireless card NDIS drivers, which use ndiswrapper as a bridging layer, are the notable exception, being in category 3. However, that's what you **can** have. What you have **by default** is entirely up to the distro. I don't know how much Ubuntu inherits Debian's default set of drivers, but I don't believe the different Ubuntu flavors have different kernels.

That's my understanding, anyway. I would encourage a subject matter expert to correct me.

---

