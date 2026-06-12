---
title: "Fix for Vmware ESX no partionable media"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by lseats on 2005-05-23
I kept getting the error "no partionalble media" and found that I had to choose the alternate SCSI virtualization -- Vmware instead of Buslogic.

---

### Post by bobs1769 on 2005-07-01
You need to switch the scsi adapter from buslogic to lsilogic and it will recognize the media.  Initially I had the same problem...  I am running esx 2.5.13.

---

### Post by Dragonmantank on 2006-07-20
This bug seems fixed in ESX 2.5.3p2. I just installed Ubuntu 6.06 Server without any issues.

---

