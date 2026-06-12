---
title: "SATA and resume from suspend to RAM"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by nmuntz on 2006-06-13
According to [http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux]("http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux"),  the patch to 2.6.15 to make resume work on SATA disks was included with the Breezy kernel.  It doesn't seem to be working in Dapper.  I've confirmed this on two different laptops with SATA.   

On resume from suspend, you'll often seen I/O errors on sda and you'll have to reboot.  Is anyone else having this problem?  The fix is supposed to be in 2.6.16.

---

### Post by nmuntz on 2006-06-13
I just checked the kernerl source for 2.6.15-23 and the patch that is supposed to fix this problem has been applied to the Dapper source. 

[http://tpctl.sourceforge.net/tmp/sata_pm.2.6.15-rc6.patch]("http://tpctl.sourceforge.net/tmp/sata_pm.2.6.15-rc6.patch")

---

