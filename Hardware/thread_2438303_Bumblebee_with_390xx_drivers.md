---
title: "Bumblebee with 390xx drivers?"
date: 2020-03-09
forum: Hardware
---

### Post by u666sa on 2020-03-09
How to install bumblebee with 390xx drivers? Standard instructions on wiki give me the latest drivers, which do not support GeForce 420M and laptop locks up after login. I need 390xx drivers, tested and tried on FreeBSD, Debian, and on Fedora, from which I'm running, got problems after latest updates, dkms does not complile with the newest kernel lul. 

Anyway, I did got it working on Debian, but haven't caught up yet on how to do it on Ubuntu.  I'm planning to stick with Ubuntu for now, I need optirun up and running.

---

### Post by CelticWarrior on 2020-03-09
You shouldn't need bumblebee.
Installing the 390 driver should also install nvidia-prime (if not install it manually). Then you should be able to switch graphics/profile with Nvidia X Server Settings. A reboot is probably needed.

---

### Post by u666sa on 2020-03-09
I have the prime-select part working. It's funky. But I want optirun, plz help me with bumblebee.

---

### Post by CelticWarrior on 2020-03-09
Bumblebee is as good as obsolete.

---

### Post by u666sa on 2020-03-09
Cool. But how do I install it with 390 drivers dkms drivers??

Or is there any other way to use intel by default and force nvidia when needed -- without reboot/

---

