---
title: "Ubuntu 6.10 or 7.04 on Alienware m7700"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by sepiid on 2007-03-26
this is the way to dual boot an alienware m7700 with hardware raid

you disable the raid.  that is the simple and elegant way of doing it.

you boot into the bios and disable the raid and you then use them in ide mode.  its been a while since i have done it ill get the exact settings for this post in a bit.

after that is done you go aobut setting up your laptop as normal.  one problem however is you cannot use the respawn dvd once you have disabled the raid.  windows simply wont boot.  so you must install from scratch.  after you have done that, then boot a ubuntu cd and process the install as normal selecting the second harddrive.

however i do mine differently.
what i do is disable raid and format both drives.
then using the a bootcd full of utilities i use FDisk to partition the first drive into two 30gig partitons. and the second drive stay whole.

on the first partition i install xp then i install ubuntu on the second 30gig partition.

then i have the second 60gig drive for storage and appinstalls on windows etc...

gone to get the bios settings, be back soon!

---

### Post by sepiid on 2007-03-26
ok first set the raid option to disabled.  then if that does not work set it to ATA.  if i recall correctly disable was the option that worked for me

---

