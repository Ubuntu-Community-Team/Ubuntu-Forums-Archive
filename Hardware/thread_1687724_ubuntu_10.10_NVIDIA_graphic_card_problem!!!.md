---
title: "ubuntu 10.10 NVIDIA graphic card problem!!!"
date: 2011-02-14
forum: Hardware
---

### Post by agathery on 2011-02-14
hi i installed ubuntu 10.10 (actually i try 10.04 and 9.04, face same problem) when i install graphic card(NVIDIA Geforge GT 320M) and restart. then there is a black screen and i cant see anythnig and cant use ubuntu! Is there anybody to solve this problem? thanks...

---

### Post by realzippy on 2011-02-14
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by oldfred on 2011-02-14
If it is a card not a chip in  a portable.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by agathery on 2011-02-14
thank for informations, i think it is a problem about optimus tech.

---

### Post by realzippy on 2011-02-15
yep.
Can you mark thread as "solved"  (Threadtools)

---

