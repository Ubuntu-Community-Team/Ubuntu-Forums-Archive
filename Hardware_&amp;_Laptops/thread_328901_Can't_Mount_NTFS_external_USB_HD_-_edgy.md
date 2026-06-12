---
title: "Can't Mount NTFS external USB HD - edgy"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by allwin on 2006-12-31
Have an old 45gig hard drive in a USB enclosure.  In order to mount it, I find that I must do a sudo rmmod ehcpci_cd command so I get the OHCP driver working.  Then I can see /dev/sda and partition /dev/sda1 show up (only has one partition on it).  When I do the sudo mount -t ntfs /dev/sda1 /media/ibm command, it says there is no boot block on the drive (this is true, I never boot from that drive and never put an MBR on it as far as I know when I partitioned it with XP long ago).

Any suggestions?  It works fine when attached to an XP system, so it's apparently formatted properly.

---

