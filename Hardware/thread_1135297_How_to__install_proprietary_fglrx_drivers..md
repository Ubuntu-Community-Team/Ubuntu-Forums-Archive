---
title: "How to  install proprietary fglrx drivers."
date: 2009-04-24
forum: Hardware
---

### Post by optimistique1 on 2009-04-24
Hi all, how do I  install proprietary fglrx drivers in Jaunty for ATI Cards as all the 'How To's' refer to 8.04 and lower.

I tried to use something called 'Envy' and that screwed the computer up so have to do a  fresh install...

Many thanks

Garry.

---

### Post by optimistique1 on 2009-04-26
Can anyone help me with this please?

---

### Post by StuartN on 2009-04-26
> **optimistique1 said:**
> Can anyone help me with this please?

You can not use earlier ATI proprietary drivers in Ubuntu 9.04, you must use the hardware driver 9.4 if your card is supported or the open source ("ati" or "radeon") drivers if your card is in the "legacy" list no longer supported by ATI ([http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English)).

Installing fglrx will break your installation because it is not compatible with the X server 1.6 in Ubuntu 9.04.

---

