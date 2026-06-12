---
title: "Hotplug....FREEZE!!"
date: 2004-12-28
forum: Hardware &amp; Laptops
---

### Post by paradox on 2004-12-28
Hi!

Hotplug just for once freeze at boot!!! Now, i think disable hotplug isn't good idea (...and loading all modules statically in /etc/modules...no?). If hotplug crash again, who i can see for undertand the problem? In this situation have a log file  for see what module cause this problem?!?

TNX!

---

### Post by diebels on 2004-12-28
Disabling hotplug is no good idea, no :)
look for hotplug in /var/log/
"sudo grep hotplug /var/log/*"

---

