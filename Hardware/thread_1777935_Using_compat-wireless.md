---
title: "Using compat-wireless"
date: 2011-06-08
forum: Hardware
---

### Post by kullerhamPster on 2011-06-08
Hi,

I tried to use compat-wireless to be able to use the wireless card of my HP G62 notebook. The notebook contains an RT5390 wireless adapter.
According to the changelog, compat-wireless-2.6.39-1-sn.tar.bz2 should contain support for this adapter.

I downloaded the appropriate tarball and followed the instructions listed here, specifying 'rt2x00' as desired driver: [http://wireless.kernel.org/en/users/Download/stable/#Building_and_installing](http://wireless.kernel.org/en/users/Download/stable/#Building_and_installing)
(I actually ommitted the point "Unloading" and rebooted first, but I don't think that's a problem).

The modules were built successfully, I added 'rt2800pci' to /etc/modules (I wonder why the instructions don't mention this step, should this happen automatically?) and the module gets loaded, but the wireless card is still not working: 'ifconfig' doesn't even list a new interface.

Did I misunderstand the purpose of 'compat-wireless'? Do I have to do something else in order to enable it?

---

### Post by kullerhamPster on 2011-06-09
*push* No ideas?

---

