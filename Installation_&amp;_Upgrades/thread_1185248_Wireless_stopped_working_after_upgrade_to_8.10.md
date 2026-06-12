---
title: "Wireless stopped working after upgrade to 8.10"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by songl100 on 2009-06-12
I just upgraded from 8.04 to 8.10. My wireless stopped working. I have a Dell Inspiron 1420 laptop. I really need help. I have a Intel Pro/wireless 3945ABG [Golan] Network Connection (rev 02) according to the Hardware test in Ubuntu. Can anyone help?

---

### Post by jim_p on 2009-06-12
Are you sure it stopped working? Open a terminal and scan for wireless networks with
```
sudo iwlist scan
```
This will verify that the module is loaded and that wireless is working as its supposed to.

If it does scan like above, dump network manager and install wicd.

(wicd is now in the jaunty repo)

---

### Post by songl100 on 2009-06-12
I installed wicd and package manager automatically removed network manager. Wireless works fine now. cool! Thanks!

---

