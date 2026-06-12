---
title: "'Boot failure' after upgrade"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by Dimas on 2008-12-05
I've an old server (7.10) and it suggested me to upgrade to 8.04 version. I've upgraded and all the operations seems to work fine, but when the upgrade finished and the computer restarts it gives an "Boot failure" error.

Some help to rescue my system? It's an important server of my company :(

Thx!

---

### Post by inobe on 2008-12-05
is it a grub error 21 ?

edit: please include some hardware information as well !

example: is it a raid array

---

### Post by Dimas on 2008-12-05
No, no grub error, its something before grub loading.

"Searching for Boot Record from IDE-0 ... Not Found
Boot Failure."

No hardware rarities, no raid... a normal desktop computer.

---

### Post by inobe on 2008-12-05
we need to verify that the system bios can see the hard drive, restart and enter the system bios to see if the ide drive is listed.

---

### Post by Dimas on 2008-12-05
This PC have an Amibios 3.31a and there aren't any devices list. But on boot menu and boot sequence I've the option HDD.

I tried to start with Hiren's CD and the partition tools detect de HDD.

---

### Post by inobe on 2008-12-05
i am starting to believe grub wasn't setup correctly during the upgrade.

here is a super grub disk that should repair the problem.

i haven't had to use it "yet" you may want to check out the wiki for additional information.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Dimas on 2008-12-05
I burned the SGD in a CDRom and booting from the PC it frozen at Loading stage2 .....

---

### Post by inobe on 2008-12-05
okay then, its all i have left

[http://ubuntuforums.org/showthread.php?t=224351&highlight=Boot+failure%27+upgrade](http://ubuntuforums.org/showthread.php?t=224351&highlight=Boot+failure%27+upgrade)

i hope it proves useful, it is the live cd method that will fix grub/ mbr

check threw all threads to verify the primary post is correct, most members tend to correct each other and the main post doesn't get edited.

edit: the thread starts at 06' eventually gets to current year 08'

---

