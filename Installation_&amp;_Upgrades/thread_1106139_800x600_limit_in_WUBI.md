---
title: "800x600 limit in WUBI ?"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by helgeo on 2009-03-25
Just installed Wubi on a 1024x768 Toshiba Portege laptop and the max screen resolution on offer is 800x600. Is there anything I can try to resolve this?
Otherwise, very impressed!

Geo

---

### Post by abn91c on 2009-03-25
thats an issue with the video card drivers, they need updating, look in the system>administration>hardware drivers, you may need to do ```
sudo apt-get install ubuntu-restricted-extras
```, it just depends what you laptop graphic card is

---

