---
title: "how can I boot in ubuntu if i install xp after ubuntu"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by enri2 on 2009-04-02
:confused:

---

### Post by oldos2er on 2009-04-02
Restore grub: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ronparent on 2009-04-02
After the winXP install boot on the ubuntu live cd.

Start a terminal session.

enter commands in terinal as follows:

sudo grub  

grub> find /boot/grub/stage1
### will find your linux grub install, then use the output to setup grub again

grub> root (hdx,y)
###  x and y are whatever you output above was.

grub> setup (hd0)
### assuming that is still your original boot drive.  The output will verify that the grub boot loader has been restored on your first drive and that the menu.list has been sucessfuly rewitten.

Reboot after removing the cd and you should be back in business.

---

### Post by enri2 on 2009-04-03
thanks guys:p

---

