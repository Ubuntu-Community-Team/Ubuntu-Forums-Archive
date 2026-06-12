---
title: "Loading iwl3945 at boot"
date: 2008-12-27
forum: Hardware
---

### Post by MadMage on 2008-12-27
Hi all!
After the upgrade to Intrepid, I had some problems with the wifi card (Intel 3945), so I tried some different solutions (i.e., backports, ipw3945 drivers, compiled from source, etc). After some month, the support people resolved the problems with the wireless card, so now I can use the iwl3945 driver shipped with ubuntu.

Now the problem is that I think I messed up things with this driver, I am able to modprobe it and everything works fine. But the driver does not load at boot, so I have to do this every time. I thought that it needed to be put in /etc/modules, but I see there very few modules, so maybe this kind of module is loaded at boot in some other way that I do not know.

What is the correct way to load iwl3945 at startup?

---

