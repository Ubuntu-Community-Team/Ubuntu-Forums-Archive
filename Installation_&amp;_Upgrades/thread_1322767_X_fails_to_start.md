---
title: "X fails to start"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by viralmeme on 2009-11-11
The system goes to a black screen when trying to boot into the GUI. It will boot to the recovery console. I did try: 'sudo apt-get --reinstall install xserver-xorg' and got 'couldn't find package xserver-org'

Native install of Ubuntu 9.10 on a 8GB USB device. I do know the USB device will boot to the 'USB startup disk creator'. Any help ?

$lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
---

update: copied over my original xorg.conf file and booted to recovery console and typed sudo gdm and it booted into the GUI. Not sure what made a difference ...
---

update: I just borked my xubuntu installation ...

---

