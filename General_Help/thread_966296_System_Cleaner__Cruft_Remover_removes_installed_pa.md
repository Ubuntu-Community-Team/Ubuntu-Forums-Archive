---
title: "System Cleaner / Cruft Remover removes installed packages"
date: 2008-11-01
forum: General Help
---

### Post by Jags_FL on 2008-11-01
After asking the forums, [**whether it is OK to remove .deb packages listed in System Cleaner**]("http://ubuntuforums.org/showthread.php?t=958182"),  when I ran Cruft Remover (under System > Administration. Earlier known as [**System Cleaner**]("http://changelogs.ubuntu.com/changelogs/pool/main/s/system-cleaner/system-cleaner_1.10.4-0ubuntu1/changelog") under System Tools) on a fresh Intrepid install, it removed/deleted all the packages that were NOT installed by Synaptic:

1, OpenOffice.org 3.0
2, Solaris Nimbus theme
3, TrueCrypt

And not just "the boxes, that held the installed programs" but they were gone/removed completely from Main Menu, AWN & from Themes (Appearance Preferences) too.

At first thought I messed up somewhere so I reinstalled them and Cruft Remover still listed 'em as unwanted and upon running CR they were gone again. CR still lists 'em after 3rd round of installations.

Is that how Cruft Remover should be removing packages or I installed 'em wrongly?  Many thanks.

---

### Post by happyhamster on 2008-11-01
- Cruft remover isn't really up to par yet. See:

[https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/285746](https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/285746)

- Running:

sudo apt-get autoremove
sudo apt-get autoclean

- once in a while, is usually sufficient to keep the system clean.

Good luck.

---

### Post by Jags_FL on 2008-11-01
Many thanks happyhamster

yes, Cruft Remover / System Cleaner in Ubuntu 8.10 ***is*** buggy. I also found similar bug on launchpad after I started the thread.

Cruft Remover removed most of the installed packages : [https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/290024](https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/290024)

---

