---
title: "linux-image-2.6.22-14-xen with fglrx on gutsy"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by scaratec on 2007-11-12
Hello everybody,

I am trying to install the propreatary fglrx driver for my ATI Mobility Radeon X1600 (on HP nx9420) in dom0. I am using the prebuild ubuntu kernel for xen (HVM).

Restricted modules for xen are installed. The driver is activate at restricted module manager. flgrxinfo still says mesa. When I use XGL flgrxinfo crashes the whole gnome session and I have to relogin.

I managed to install the driver without xen serveral times. Even the compiz stuff worked fine without the xen-kernel. So I know the basics. But when it comes to xen I failed to install the driver.

I even tried to install the latest driver from ATI which should actually work with AIGLX. But whenever I tried to build the module, it failed due to an unknown architecture.

Can anybody help me to make xen working with my ATI Mobility Radeon X1600?

Regards
Randy

---

### Post by sarantos on 2008-01-08
I am also trying to use xen on a HP nx9420, but fglrx fails.
If you - or anybody else - managed to get more progress, please let me know.

Sarantos

---

### Post by fogster on 2008-01-15
Anyone come across anything yet?

I'm running Gutsy and had a nice desktop setup with fglrx and Compiz (X1300 Mobility here). If I boot into the Xen Dom0 kernel, fglrx doesn't load.The  Restricted Drivers Manager shows it, but says "Not in use."

The desktop is painfully slow without it, and has some bizarre graphics glitches.

Is it just a case of the kernel not supporting it? It's driving me batty!

---

### Post by fogster on 2008-01-15
Another thread I found references needing xen-restricted-modules, but...

The only package I see is xen-restricted-modules-2.6.17. This does provide fglrx (among others), but unsurprisingly, it doesn't work, since it's for an older kernel and a 64-bit platform:

```
xen-restricted-modules-2.6.17-6-generic-xen0:
 Depends: xen-image-xen0-2.6.17-6-generic-xen0  but it is not installable
```

The more I Google, the more I find more people having the same problem, not just on Ubuntu. It seems that fglrx (or any restricted video drivers, really) don't play nice with Xen. (And I mean dom0, not inside a VM.) And yet the occasional post makes it sound as if it's doable.

Someone must have gotten this to work?

---

### Post by fogster on 2008-01-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/151327](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/151327) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				In the interest of keeping this thread up-to-date, this is covered by bug 151327, which seems to date back to October. :frown:

---

