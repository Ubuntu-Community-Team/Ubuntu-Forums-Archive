---
title: "Dual Boot Install"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by ktyson on 2009-01-25
I am totally new to this environment and to creating a dual boot system.  I have two hard drives, one is a 250Gb drive partitioned to C: and D: drives the other is a 150Gb partitioned as one drive.  My first attempt was to install Ubuntu on the empty 150Gb drive.  The install seemed to go fine but when I did the restart it booted right into Windows XP, no grub.  So I thought perhaps that I need to install it on the drive that has the original boot record.  I moved everything off of D: and restarted Ubuntu live CD.  My problem now is that if I go with the "guided" install it defaults to install it on the second drive.  How can I create my dual boot for Windows XP and Ubuntu?

---

### Post by ktyson on 2009-01-29
Well, I feel dumb.  All I had to do was change the boot order so the system looked to the drive with Ubuntu on first.

---

