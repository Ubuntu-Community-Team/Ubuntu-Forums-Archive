---
title: "Very odd NTFS mount error - Includes screenshot"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2007-07-28
I have an external hard drive, USB.  It has had no problem with ubuntu, but after connecting to a windows PC once, then connecting it back to my home PC, I get this error.

Oddly enough, this error does NOT appear on my ubuntu laptop.

I was able to get over this error once by uninstalling any NTFS related modules from ubuntu via synaptic, then reinstalling them.  The hard drive was accessed perfectly the next time around.  But today, one boot later, the same error is appearing, and I it hasn't been connected to any other PC but this one since I fixed it yesterday.

Any ideas?

---

### Post by bbzbryce on 2007-07-28
Have you tried doing what the message suggested? It seems like your NTFS volume is screwed up. Try reconnecting to a windows machine and disconnect properly. If you already did that then maybe the external drive is screwed up and it doesn't disconnect properly.

Assuming disconnecting in windows properly fixes the problem, I think it would be nice if the Linux NTFS driver could correct this problem, but I guess it's just not that advanced.

The best advice of course is don't use NTFS.

---

### Post by diablo75 on 2007-07-28
I chose NTFS for compatability reasons, because I plan to use this hard drive with lots of different PC's, different OS's.

---

### Post by diablo75 on 2007-07-28
I got it fixed.

Using VMware, I installed a USB controler to the guest OS, and loaded Windows.  It detected all the hardware correctly, and then I went through the Safely Remove Hardware routine, and it did its thing.  Then I shut down that OS.  The drive mounted with no problem after that.

---

### Post by bbzbryce on 2007-07-28
> **diablo75 said:**
> I got it fixed.

Using VMware, I installed a USB controler to the guest OS, and loaded Windows.  It detected all the hardware correctly, and then I went through the Safely Remove Hardware routine, and it did its thing.  Then I shut down that OS.  The drive mounted with no problem after that.

External hard drives are a pain sometimes. Despite being a weird errror message at least it was informative. Rather than something simple like "mount error."

---

