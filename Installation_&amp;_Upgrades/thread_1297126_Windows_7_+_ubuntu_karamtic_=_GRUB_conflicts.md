---
title: "Windows 7 + ubuntu karamtic = GRUB conflicts ?"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by epicwallpaper on 2009-10-21
So I'm thinking about doing a fresh install of ubuntu 10.04 and windows 7 on my laptop because ubuntu 10.04 uses GRUB2 will there be any GRUB conflicts?

---

### Post by stlsaint on 2009-10-21
win 7 doesnt use grub so may i ask what grub conflicts do you mean?

---

### Post by Mark Phelps on 2009-10-21
> **epicwallpaper said:**
> So I'm thinking about doing a fresh install of ubuntu 10.04 and windows 7 on my laptop because ubuntu 10.04 uses GRUB2 will there be any GRUB conflicts?

First of all, there is no 10.04.  So, do you mean 9.04 (the current released version), or 9.10 (the one to be released the end of this month)?

It's going to be a challenge to get working, though, because if you install 7 first, to an unformatted drive, it will install two partitions, the first one being a new BOOT partition, and folks attempting to dual boot that setup with Ubuntu are reporting an inability to get it working.

If you install Ubuntu first, and then install 7, I don't think it will use the new BOOT partition approach (don't know for sure, haven't tried that), but it WILL overwrite the MBR.  After that, you'll have to boot from an Ubuntu liveCD and reinstall GRUB.  Also, Ubuntu won't know about 7 (because it did not exist when you installed Ubuntu), so you will have to hand-build the GRUB entries.

Finally, if this isn't enough to deal with, Ubuntu 9.10 uses GRUB2 -- which doesn't use the traditional menu.lst approach for booting GRUB anymore. So, it may be difficult to get the details needed to hand-edit the script files to add OS selection capability for 7 to GRUB2.

---

