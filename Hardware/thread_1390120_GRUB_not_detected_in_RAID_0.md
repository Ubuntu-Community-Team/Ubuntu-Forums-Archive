---
title: "GRUB not detected in RAID 0"
date: 2010-01-25
forum: Hardware
---

### Post by REDace0 on 2010-01-25
Here's a brief summary of my system and the problem. I have an Asus M4A79T Deluxe mobo with a 1TB RAID 1 and a 160GB RAID 1. This mobo uses an AMD hardware RAID controller. Windows and all of my media and documents live on the 1TB array. On the 9.10 64-bit LiveCD Ubuntu correctly detects both arrays with no problems. I proceed to install Ubuntu to a 72GB partition on the 160GB array with an 8GB swap partition. Install completes normally, but when I try to boot from the 160GB RAID array, my BIOS complains that there is no bootable media there.

I have tried installing GRUB in "(hd0)", whichever drive that's referring to, the Windows partition in the 1TB array, and the 160GB array. In the above cases when I try to specify the smaller array as the primary boot hd, the BIOS can't find GRUB; when I specify the larger array as the primary, Windows loads normally. Is there a very specific drive I have to put GRUB on? Does GRUB require special configuration?

---

