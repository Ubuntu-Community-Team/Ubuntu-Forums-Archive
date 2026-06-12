---
title: "Un-dual boot"
date: 2008-11-11
forum: General Help
---

### Post by wildman4god on 2008-11-11
If you dual boot ubuntu and another linux distro but now who like to be rid of the other linux distro, how do you remove that partition with out affecting your main ubuntu installation?

---

### Post by giuspen on 2008-11-11
1) if the grub is into the boot partition of the distribution u keep => u have no problems to delete the other distributions (do it from the ubuntu livecd - system - administration - partition editor)... in case u mounted some partitions that now u deleted => sudo gedit /etc/fstab and delete from the text file that partitions
2) if the grub is on the boot of the distribution that u delete:
[http://open.vitaminap.it/en/linux_howtos.htm#grub]("http://open.vitaminap.it/en/linux_howtos.htm#grub")

---

