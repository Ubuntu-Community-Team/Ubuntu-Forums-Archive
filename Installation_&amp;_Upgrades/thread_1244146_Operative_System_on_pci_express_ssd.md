---
title: "Operative System on pci express ssd"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by livevil on 2009-08-19
Hi guys! I would install ubuntu on a pci express ssd on my laptop to save battery and use hd just for data storage. Is it possible? The pc can boot from pci express ssd? Thank you.

---

### Post by dstew on 2009-08-19
> The pc can boot from pci express ssd?Only your PC maker can tell you that. It seems that some laptops and PCIe devices will create interfaces that run as SATA or ATA, and these might boot, but some run as USB, and these might not boot. In particular the MiniPCI Express form factor will usually behave as USB. [See this forum thread]("http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=5233&forum=18").

---

### Post by presence1960 on 2009-08-19
> **dstew said:**
> Only your PC maker can tell you that. It seems that some laptops and PCIe devices will create interfaces that run as SATA or ATA, and these might boot, but some run as USB, and these might not boot. In particular the MiniPCI Express form factor will usually behave as USB. [See this forum thread]("http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=5233&forum=18").

+1

I helped someone in a thread who installed an OS to a disk connected to one of those cards but the OS would not boot. The solution was to plug the optical drive into that card and the hard disk into the mobo connector and voila! the OS booted right up.

---

