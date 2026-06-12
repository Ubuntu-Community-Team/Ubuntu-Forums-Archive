---
title: "Installation"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by Specials on 2009-02-23
Hey I have a really big proble. I was upgrading my laptop to the new version of the unbuntu 8.04. As I was installing the upgrades and I accedentally shut down my computer during the process. and now when I try to log back in it tells me that I X server is dont detected. If anyone has any good Ideas to help me with this problem please let me know.
Thanks,

---

### Post by Partyboi2 on 2009-02-23
When you are at the login screen press Ctrl+Alt+F2 to take you to a terminal, then try 
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

