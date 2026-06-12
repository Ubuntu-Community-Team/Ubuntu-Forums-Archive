---
title: "Networked installs and CD installs"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by kartikvashishta on 2009-04-28
Installation of Ubuntu may not significantly differ from installation of Solaris. To, among other things, test networked installs, CD installas, GRUB, PXE, networking, pci cards, device drivers, on some of my Solaris 10 systems I created a free root account. YOU WILL, AS USER 'unix' TELNET TO ONE SYSTEM, THEN, FROM THERE, AS "root" you will telnet to any of three other systems. The system you will telnet to first is: trainingzone.getmyip.com once there, you may telnet to any of these systems: AELLIP , AALOROTOM, NAUEEREEFS, CBSH
You may install software, install patches, install zfs filesystems(using makefiles).
so, first:
telnet trainingzone.getmyip.com
username: unix (no password, hit enter)
Then, telnet to any/all of: AALOROTOM, NAUEEREEFS, CBSH
example: telnet AALOROTOM 
AND/OR
telnet AELLIP 
username:root
password (hit enter)
username: root (no password, hit enter)
Full training(free): [http://www.kartik.com/FreeUNIXTraining.html](http://www.kartik.com/FreeUNIXTraining.html) updates on accounts will be made here.
Kartik Vashishta

---

