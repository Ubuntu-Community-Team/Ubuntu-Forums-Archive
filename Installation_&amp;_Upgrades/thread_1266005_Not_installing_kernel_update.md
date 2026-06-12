---
title: "Not installing kernel update"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by yusuo85 on 2009-09-14
when ever I try installing the newest kernel via upgrades it keeps on coming up as a blocked update, one of the updates as i cant remember all of them is called "linux-image-2.6.28-15-generic" no matter what i do it wont allow me to unblock this update.
When i was using gnome it allowed me to install this no problem but now i've fresh installed kde it just wont allow it, any ideas

---

### Post by Partyboi2 on 2009-09-14
Hi, open a terminal and try
```
sudo apt-get dist-upgrade
```to upgrade the block package.

---

### Post by yusuo85 on 2009-09-14
thanks done the job perfectly

---

