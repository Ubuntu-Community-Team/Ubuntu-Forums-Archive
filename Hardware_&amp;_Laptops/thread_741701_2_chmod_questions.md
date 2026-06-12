---
title: "2 chmod questions"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by CoffeeBreath on 2008-04-01
I see that I can chmod a NTFS usb drive so that I can use it without being root. (ntfs-3g). But, I'm not interested in having non-root access given every time I plug in a different NTFS drive. 
1. Can I set permission on a drive by drive basis rather than for all NTFS drives that are plugged in?

I've seen that I can accomplish this by doing:
sudo chmod 4755 /usr/bin/ntfs-3g

2. But why 4 digits? Why not chmod777?

---

### Post by cmnorton on 2008-04-01
You are setting userid for root on that program.

---

