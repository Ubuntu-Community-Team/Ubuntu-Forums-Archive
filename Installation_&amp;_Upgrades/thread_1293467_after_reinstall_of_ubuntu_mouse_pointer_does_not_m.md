---
title: "after reinstall of ubuntu mouse pointer does not move"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by thomaskprakash on 2009-10-17
hi,
i reinstalled ubuntu in order to solve the bootloader problem with windows.

the final install was ubuntu 9.04. But on restart after install, my mouse pointer just stays where it is without any response.

How can i make my ps/2 mouse work in ubuntu ?

please help
thomaskprakash

---

### Post by tommcd on 2009-10-17
Were you using Ubuntu 9.04 before you reinstalled Ubuntu, or was it a different version?
Anyway, try opening a terminal and run this:
```
sudo dpkg-reconfigure console-setup
```
Then reboot with "sudo reboot".

---

