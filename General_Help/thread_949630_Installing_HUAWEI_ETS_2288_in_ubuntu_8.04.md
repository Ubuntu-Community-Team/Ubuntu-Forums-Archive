---
title: "Installing HUAWEI ETS 2288 in ubuntu 8.04"
date: 2008-10-16
forum: General Help
---

### Post by John Mukulu on 2008-10-16
Getting HUAWEI MODEM Working on UBUNTU 8.04
[LIST]
[*]First find restricted packages that comes with ubuntu 7.10 by default, or find 7.10 image, and add its repositories in synaptic package manager.
[*]Then install the packages, i'm not sure which exactly does get the modem working but, install the packages that has to do with network.
[*]Edit the dialing rules in "/usr/udev/rules.d/" or path like such, i'm not sure, you should be able to change the rules, it has been posted in other forums.
[*]Then edit the ppp0 rules, and you are good to roll.
[*]How ever the above steps have one problems, you'l have to plug the modem before booting to get it working, if you unplug it in the middle, the rules corrupt, i havent fugured the solutio for that problem lately.
[/LIST]

---

### Post by smartboy08 on 2008-11-29
How it can be installed on Ubuntu 8.10

---

