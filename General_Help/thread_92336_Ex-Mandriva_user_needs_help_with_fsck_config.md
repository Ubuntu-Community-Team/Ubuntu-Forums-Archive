---
title: "Ex-Mandriva user needs help with fsck config"
date: 2005-11-19
forum: General Help
---

### Post by kalahari875 on 2005-11-19
Hello all. I recently replaced my Mandriva 2005 LE installation with Kubuntu 5.10 and so far am very happy with it. In Mandriva, I had it configured to automatically run fsck on boot when it detected that it needed to (e.g. the server lost power and rebooted abruptly when the power came back on) by editing /etc/sysconfig/autofsck and setting:
  AUTOFSCK_DEF_CHECK = yes

How do I set this same thing up in Ubuntu? :confused: Thanks.

---

### Post by blueplazma on 2005-11-19
My understanding of ext3 (the FS used in Breezy) is that it can automatically recover when it comes back up, even if it lost power.  If you do ever lose power, you will notice it checking the journal.  Anybody know for sure?

---

### Post by kalahari875 on 2006-04-22
I had a power failure recently and indeed it does check when it reboots. However, it does NOT automatically repair all the errors like Mandriva did. Instead, it made me answer 'Y' dozens of times for each error it detected in the filesystem. Is there no way to automatically have the detection AND all necessary repairs done upon reboot?

---

