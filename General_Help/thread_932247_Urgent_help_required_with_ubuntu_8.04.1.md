---
title: "Urgent help required with ubuntu 8.04.1"
date: 2008-09-28
forum: General Help
---

### Post by kevdoc on 2008-09-28
Hey guys, really really need help here. I was having problems with my screen resolution and was followingsome of the suggestions on this and other forums when my computer just won't boot properly now.

I have a webbook which has no drives with which to reinstall and was wondering if anyone can help me.

After the ubuntu sign appears to be fully loaded i get this script after pressing ctrl-alt-f1

[I]Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/7547d25e-b5d9-4f92-b88e-e3bb68968d98) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/7547d25e-b5d9-4f92-b88e-e3bb68968d98
kinit: No resume image, doing normal boot...

Ubuntu 8.04.1 ubuntu tty1

ubuntu login:[/I]

Then, if i just leave it wothout pressing ctrl-alt-f1 then it'll sit and do nothing.

Anyone who could help would be amazing

Cheers

Kev

---

### Post by kokkus on 2008-09-28
So it boots but GDM (the login screen) doesn't come up?
It could be gdm is disabled. If so, you can start recovery mode and from shell command you type this code to start it again: 
```
sudo mv /etc/rc2.d/s30gdm mv /etc/rc2.d/S30gdm 
```

If this is a package bug,
from recovery mode you can try to fix broken packages
(Insert the cd before you do this)
From shell you can try sudo --fix-missing

If the screen problem came because of Compiz or han another graphical reason, you can from recovery mode try to fix the x server, and enable your graphic card when you are inside ubuntu again.

---

