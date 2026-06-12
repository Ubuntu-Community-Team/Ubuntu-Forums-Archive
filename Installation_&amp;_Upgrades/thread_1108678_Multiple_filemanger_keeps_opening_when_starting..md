---
title: "Multiple filemanger keeps opening when starting."
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by presso on 2009-03-27
I have just tried installing Jaunty (9.04) via vmware but when it loads up there seems to be an endless loop of file manager opening. Has anybody else come across this problem and how would i go about fixing this. Version 8 i have no problem with at all but would like to move up to 9 as you do. 
I have included a ss of my task bar to show what i mean.

---

### Post by mtapman on 2009-03-28
Same issue here. Install details:

Host: Fedora (2.6.27.19-170.2.35.fc10.x86_64)
VMware: Workstation 6.5.1 build-126130
Guest Install Media: ubuntu-9.04-beta-desktop-i386.iso
Guest: Ubuntu 9 Beta (2.6.28-11-generic)
Install process: default U.S. language installation in an 8GB drive

Disconnecting the CD-ROM (mapped to the ISO image still) fixed the problem. Reconnecting the CD-ROM caused the problem to start again. Changing the CD-ROM device mapping from the ISO image to the physical CD-ROM drive, in my case /dev/sr0, allowed me to reconnect the CD-ROM to the Ubuntu 9 Beta guest.

---

### Post by presso on 2009-03-28
Nice thanks for that will give it a shot.

---

