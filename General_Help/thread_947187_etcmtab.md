---
title: "/etc/mtab"
date: 2008-10-14
forum: General Help
---

### Post by sulekha on 2008-10-14
why is it said that /etc/mtab file should not be deleted ?

---

### Post by Sam on 2008-10-14
The /etc/mtab file lists all the mounted filesystems and is modified in real-time. You should probably not delete it, it may cause trouble to the system...

---

### Post by trickytoad on 2008-11-09
hi,

I modified my mtab file for some reason, now i cannt boot my system. Luckly, i took a back up of my mtab file before altering, but i cannt restore it back in recovery mode. While i am trying to restore it throws my the following error.

[file system is readonly].

Please do help wat i wanna do restore my system???

---

### Post by trickytoad on 2008-11-10
please help my system is down coz of the above problem........ [:(]

---

### Post by trickytoad on 2008-11-12
i myself resolved it problem by doing the following ...

While booting select the recovery mode and select the root to get the prompt with root privileges and then i replaced my mtab file.

typed reboot to restart the machine, then i got my ubuntu back :)

---

