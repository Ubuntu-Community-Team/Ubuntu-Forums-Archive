---
title: "Installation Issue"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by Leventcos21 on 2009-06-02
Hi, I am trying to install Ubuntu on a Amd XP-M and I receiving this error message:
```
 
xstaruperror, "x server exited with return coe" + str
Type: nonetype object is not iterable

```
It then coems to this [EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] prompt.
512MB, 80GB HD
I error checked the disk and it says that it is fine.
I partitioned the HD ext3

---

### Post by utnubuuser on 2009-06-03
Tried reinstalling the xserver?
from that prompt:> sudo apt-get install --reinstall xserver-xorg-core
or maybe it's just a matter of reconfiguring the xserver with> sudo dpkg-reconfigure xserver-xorg

---

### Post by spcwingo on 2009-06-03
Try booting in "safe graphics mode".  If that doesn't work, try the alternate CD:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

If neither work...let us know.

---

