---
title: "Innonex Virtualbox"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by uttaran on 2008-12-03
I've installed innonex virtualbox and want to run WinXP virtually.But when i attempt to start the virtual system it says

[B]The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).
[/B]
What to do???????????

---

### Post by squaregoldfish on 2008-12-03
The usermod program can alter a user's groups and permissions. To add a user to the vboxusers group, enter the following:

```
sudo usermod -a -G vboxusers <username>
```

Steve.

---

### Post by uttaran on 2008-12-04
Thanks.Now tell me how to mount my existing hard disk partitions in that virtual system.........it only shows the virtual hard disk.


Tell me how to find the questions i've posted in this forum quickly

---

