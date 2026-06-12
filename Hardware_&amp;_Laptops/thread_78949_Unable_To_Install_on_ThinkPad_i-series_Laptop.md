---
title: "Unable To Install on ThinkPad i-series Laptop"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by jpass on 2005-10-19
I've tried to install the latest ubuntu release on my ThinkPad i-series laptop, and it's failing early in the installation process.  The laptop itself is strange because while IBM documented it on their support site, the configuration they report wasn't what I bought in the store.  (The laptop has a larger screen and bigger hard drive than IBM's support site said it has, and came with different software.)

Regardless, the laptop's bottom sticker says it's a 2611-451, and if I remember correctly, it was sold as a "i1451".

During installation, the installer stops during the load of the "ide-cd" (at 86%).  My guess is that there actually isn't any problem loading this device driver, but some prior driver has screwed up the IDE channel, making the load of this driver fail.  I haven't yet tried to disable other drivers prior to the ide-cd to verify this, in part because I don't know which drivers are used.

I've had this problem with other Debian-based distributions, and random installation problems with Mandrake and RedHat.  I've never had any problem installing different flavors of Windows (98, 2000), presumably because their installers either don't probe for hardware the same way.

Any help would be appreciated.

---

### Post by penguintiz on 2005-11-22
Hi,
I ran into the same problem. Try typing this at the prompt:
linux pci=noacpi
(You can get the info by pressing F1 and then F7 at the boot screen)

---

