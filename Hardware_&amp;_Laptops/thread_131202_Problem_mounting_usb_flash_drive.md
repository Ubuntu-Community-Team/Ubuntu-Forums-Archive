---
title: "Problem mounting usb flash drive"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by jsvidyad on 2006-02-15
Hi!!!


   I have difficulty mounting my usb flash drive. When I insert the flash drive, it is detected when I check Places -> Computer. But, when i try to mount it manually, by right clicking and selecting Mount Volume, I get an error message saying
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount

  I have breezy installed on a computer in my lab and there the flash drive is automatically mounted when I insert it without any problems.  If I remember correctly, when I installed breezy, initially the usb flash drive was mounted automatically.

  Thanks in advance for any help.:cry:

---

### Post by jsvidyad on 2006-02-18
Well, the problem has been resolved, though not entirely not to my satisfaction. After adding a line to my fstab, the flash drive can be mounted provided I plug it in before booting.

---

### Post by wolfie on 2006-02-25
What was the line that you added?

---

