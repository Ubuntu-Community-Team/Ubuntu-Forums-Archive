---
title: "USB harddisk suddenly has I/O errors"
date: 2005-10-04
forum: Hardware &amp; Laptops
---

### Post by g-joey on 2005-10-04
Hi folks,

I'd like to create backups of my HDD using external HDDs which are installed in an USB drive cage.

After I've switched on the cage and plugged it into a USB port, I could create a partition as **/dev/sda1**, make an ext3 file system and mount it without any problems.

But during the backup (app. 70 GB), after having copied app. 10 GB, I get endless "I/O error"s. The HDD is unmounted and the device **/dev/sda** is no longer available.

After I have switched off an on the USB cage, the device is there again, but **fsck **reports a corrupt filesystem...

Any ideas what I can do now?

// Joe

---

