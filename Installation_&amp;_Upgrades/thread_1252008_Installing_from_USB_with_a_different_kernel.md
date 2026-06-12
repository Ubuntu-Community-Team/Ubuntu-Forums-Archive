---
title: "Installing from USB with a different kernel"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by elmosim2 on 2009-08-28
I've installed with a USB drive before and it has worked beautifully.  The problem I have is the kernel that is installed is 2.6.28.  This kernel has a known issue with my SDHC card reader in my dell mini 9.

I was hoping to install right onto the SDHC card, but Ubuntu doesn't even recognize it (in nautilus and gparted).  Is it possible to change the kernel that is being installed from a USB drive?

---

### Post by mikewhatever on 2009-08-28
You could try installing a different release, all of which have different kernels, Hardy 2.6.24, Intrepid 2.6.27, and Karmic 2.6.31-rc. I can't really recommend Karmic, since it hasn't been released yet, but if all fails, it is an option.

---

### Post by snowpine on 2009-08-28
You can't install to a SDHC card on the Dell Mini 9, because the Mini 9 can't boot from it.

---

### Post by elmosim2 on 2009-08-28
In that case.  If I do end up getting it installed on the internal disk and can use the SDHC card as storage.  Can I use the space on that for installing programs?  The actual problem is that I run out of space on the 8GB internal storage flash

---

### Post by snowpine on 2009-08-28
Mmmm I think you can mount certain system folders to the card, but I wouldn't recommend it, because then the computer is useless if you remove the card. :) Better to install the OS (and applications) on the internal drive and use the SDHC for documents.

---

