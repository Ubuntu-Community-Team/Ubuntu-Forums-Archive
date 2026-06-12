---
title: "[SOLVED] Reinstallation?"
date: 2008-08-25
forum: General Help
---

### Post by Yezinki on 2008-08-25
Hi there,

Using a dual boot, with imaging already done, hypothetically if one of my Os ie Ubuntu gets messed up......how do I reinstall?

Using the same Live CD?.....it shall automatically get installed in the /root partition, with settings saved in /home automatically be applied?

Thanks!

---

### Post by mikewhatever on 2008-08-25
No, it will not install automatically. You'd have to point it to all three partitions, /, /home and swap, using the manual partitioning option. You'd have to know which /dev/sdX is which and it's worth taking a note before reinstalling. Once that is done, and you proceed, the system will get installed into / which will be formatted, and settings will be applied from /home.

---

### Post by Yezinki on 2008-08-25
Thanks very knowledgeable person I appreciate your comments!

---

