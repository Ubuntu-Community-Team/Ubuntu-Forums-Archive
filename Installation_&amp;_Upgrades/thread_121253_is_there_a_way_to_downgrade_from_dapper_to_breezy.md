---
title: "is there a way to downgrade from dapper to breezy"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by yarikoptic on 2006-01-24
I have a fresh PowerBook G4 which didn't want to boot from CD/DVD with breezy installation. Recent Dapper worked but now I can't setup dual video display nomater what I have tried. People seems to don't have problem with radeon with previous release of Xorg which is shipped with Breezy. So I am thinking may be to install breezy while running dapper. Do you think that next scheme would work (or fail)

Install breezy within a chroot environment.
Boot from Dapper install CD for the sake to get to the drive
Move /etc,/var, /lib, /usr from chroot so on the next boot I have breezy Ubuntu running...

Or this way is doomed?
Thank you in advance!

---

### Post by xalen on 2006-04-29
You can follow this link but it looks like it's better just to do a fresh install: [http://riceball.com/drupal/?q=node/282](http://riceball.com/drupal/?q=node/282)

---

### Post by yarikoptic on 2006-04-30
actually I just debootstrapped breezy into another partition and that was it - it worked without any problems. After I got satisfied with breezy install, I wiped out partition with dapper

---

