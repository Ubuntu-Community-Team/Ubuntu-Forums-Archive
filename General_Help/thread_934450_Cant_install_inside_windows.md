---
title: "Cant install inside windows?"
date: 2008-09-30
forum: General Help
---

### Post by mmmmf on 2008-09-30
ok so i installed ubuntu 8.04 inside windows. it seemed to install fine, but now every time i boot into ubuntu it starts checking my partitions as if it wants to install again? anyway it freezes everytime, it just says its checking my partitions (ive only got 1) and it just sits there not doing anything as if its completely frozen. is this a common problem? its really confusing and frustrating.

---

### Post by Sef on 2008-10-03
Moved to Wubi forum.

---

### Post by Orlsend on 2008-10-03
Huh Funny WUBI does not use Partition method it only creates virtual disk's, In windows under the Ubuntu folder can you tell me what you got?

---

### Post by monkeystuner on 2008-10-03
That does sound odd. I would try uninstalling Ubuntu, defragment your HDD and then reinstall but make sure you leave plenty of space for the install. You also my try running a chkdsk in before you reinstall to make sure everything ok with that HDD.

---

### Post by ago on 2008-10-06
If you go to a terminal (ctrl+alt+f3) you can check the log in /var/log/syslog. Please report any error message. If you can copy the full log to your windows partition (available as /host OR /isodevice) and post it here.

---

