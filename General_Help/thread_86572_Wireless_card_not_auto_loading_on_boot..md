---
title: "Wireless card not auto loading on boot."
date: 2005-11-05
forum: General Help
---

### Post by loon on 2005-11-05
Don't know why, but I have an eth0 and an eth1 (wireless cisco aironet) but Ubuntu made a eth2 which is my wireless?? However, the eth2 doesnt auto load on boot and I have to activate it each time I login.


Any ideas??  Thank you.


- loon

---

### Post by taurus on 2005-11-05
You can look in /etc/network/interfaces.

---

### Post by Plank117 on 2005-11-05
Try ```
ifconfig eth1
``` to see if it even exists.

---

### Post by Plank117 on 2005-11-05
You should probably take this to Hardware Help. They'll be able to help you.

---

