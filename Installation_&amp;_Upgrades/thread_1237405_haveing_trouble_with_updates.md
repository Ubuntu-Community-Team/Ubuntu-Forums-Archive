---
title: "haveing trouble with updates"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by invitingdopeman on 2009-08-11
thanks for the reply on my other post yea windows is totally different im haveing trouble with the up dates i have included a screen shot it says i have to go in mannually and do it but it wont let me please help and thanks INVITINGDOPEMAN

---

### Post by gabry79Italy on 2009-08-11
open a terminal and run:
sudo dpkg --configure -a

---

### Post by invitingdopeman on 2009-08-11
alright thanks man is that all i do????

---

### Post by gabry79Italy on 2009-08-11
sudo -s
apt-get update
apt-get upgrade
exit

---

### Post by drs305 on 2009-08-11
> **invitingdopeman said:**
> alright thanks man is that all i do????

That's all you should need, then update. If not, post the error messages.

---

