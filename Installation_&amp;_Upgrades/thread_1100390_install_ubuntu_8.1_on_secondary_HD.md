---
title: "install ubuntu 8.1 on secondary HD"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by rawegg on 2009-03-19
I have WinXP Sp3 on my primary hard drive (IDE SATA I) and wish to install ubuntu on my second HD (SATA II) thus far unformatted.

Bios recognizes both hard drives.  When I set the boot order to the new secondary drive it tries to boot, can't, and asks for a boot disk.

I give it the ubuntu installation CD and it boots up to ubuntu.

All is good EXCEPT ubuntu wants to install onto my XP hard drive (/dev/sda).  I can see the second HD (/dev/sdb) on the ubuntu drop down list of devices.

How do I get ubuntu to install onto my secondary hard drive?

---

### Post by Al Fischer on 2009-03-19
How about simply unplugging the primary? (you only need to remove the power connection)

---

### Post by rawegg on 2009-03-19
> **Al Fischer said:**
> How about simply unplugging the primary? (you only need to remove the power connection)

I thought of that, but I guess I was looking for something a little more elegant.  I suppose once ubuntu is installed bios will boot whatever disk is called first.  I think I just talked myself into trying your suggestion.:D

---

