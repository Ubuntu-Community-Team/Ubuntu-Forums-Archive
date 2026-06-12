---
title: "Disk Manager / Kernel remap 63"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by raudette on 2006-02-23
I'm running Ubuntu Breezy Badger, which installed kernel 2.6.12-10-386

I have a hard drive with the Ontrack Disk Manager DDO, and I can't seem to use the "remap63" option I see all over the web.

My grub kernel entry is as follows:
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 hdb=remap63 ro quiet splash

Thoughts?

Richard

---

### Post by lonewolf72 on 2006-03-01
i too am having this problem...  the hard drive is an old one out of a crashed 486... but the data is important

---

### Post by raudette on 2006-03-07
In the end, I could not get the remap63 kernel parameter to work.

I borrowed a hard drive, booted a system rescue CD with a 2.4 kernel (which does work with the disk manager).

I copied the data from the original drive with disk manager to the borrowed drive, then removed disk manager & reformated the original drive, and copied all of the data back.

And that worked.

---

