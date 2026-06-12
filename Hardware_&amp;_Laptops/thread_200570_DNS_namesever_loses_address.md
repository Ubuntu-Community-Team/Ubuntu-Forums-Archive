---
title: "DNS namesever loses address"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by wiljohnson on 2006-06-20
Followed installations for Netgear WG511 v2 and was able to connect however after a reboot I get 'cannot find server'.  I check /etc/resolv.conf and find the address has changed to 0.0.0.0   Entering the address again allows me to connect until reboot and once again entering address allows

---

### Post by Burnout on 2006-06-22
Probabely your dhcp server gives a wrong dns address to your pc. Try to manually set the dns server address and disable the dns server on your router.

---

