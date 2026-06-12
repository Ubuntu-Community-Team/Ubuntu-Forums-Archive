---
title: "Swapping even if there is still enough RAM left"
date: 2008-09-12
forum: General Help
---

### Post by j0natz on 2008-09-12
Hi, 

I'm wondering if you can explain something to me.

Right now I'm using 35 % of the available ram. (Which is 354 MB of 1 GB)

Even if there is plenty RAM left he swapps 200 MB to the swap partition.

Can I change this so he uses RAM instead of my HD?

Thanks!

Jonas

---

### Post by 3rdalbum on 2008-09-12
```

sudo swapoff -a
```

---

### Post by j0natz on 2008-09-12
Thank you!

What happens if I'll ever get the rams full?

KR

Jonas

---

### Post by plucky on 2008-09-12
Try changing the "swappiness" parameter ```
gksudo gedit /etc/sysctl.conf
``` and add ```
vm.swappiness=0
``` to end of file.

Reboot

Good Luck

---

### Post by WRDN on 2008-09-12
While finding the swappiness level you want (between 0 and 100), you can use the command:

```
sudo sysctl vm.swappiness=X
```

X represents the swappiness value. To make the change permanent, do what plucky advised above.

---

### Post by anotherdisciple on 2008-09-12
Turning your swap off would make you unable to hibernate. I would just adjust the swappiness like they mentioned above.

---

