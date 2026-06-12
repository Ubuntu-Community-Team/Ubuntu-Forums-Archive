---
title: "Installing GRUB"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by Felix Lionheart on 2009-01-20
Hello, I formatted and reinstalled Windows Vista to find out that it deleted GRUB meaning I can't boot Ubuntu. Is it possible to install or recover GRUB?

---

### Post by taurus on 2009-01-20
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by stefangr1 on 2009-01-20
Yes, you can use the installer cd to do that. You open a terminal and type:

sudo grub

and search for the location of your boot partition:

find /boot/grub/stage1

Then you do:

setup (hd0)

to reinstall grub (change the 0 to the disk that was given in the previous step)

and exit the program with "quit"

---

### Post by Felix Lionheart on 2009-01-20
Thanks

---

