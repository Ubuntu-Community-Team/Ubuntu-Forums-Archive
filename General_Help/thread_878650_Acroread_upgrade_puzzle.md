---
title: "Acroread upgrade puzzle"
date: 2008-08-03
forum: General Help
---

### Post by Pete051 on 2008-08-03
Hi people
I've installed hardy heron of both my desk top and laptop computers, both work perfectly apart from one small problem that recently appeared on the laptop.
Adept notifier tell me that there is an upgrade for acroread and acroread plugins but when I try to upgrade Adept tells me the packets are broken yet it keeps on telling me to upgrade.
There is no problem at all on the desk top.
Any ideas anyone?
Regards
Pete

---

### Post by sayakb on 2008-08-03
At a terminal, type in:
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Pete051 on 2008-08-03
No afraid not this is the terminal readout:
pete051@pete051-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  acroread acroread-plugins
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

