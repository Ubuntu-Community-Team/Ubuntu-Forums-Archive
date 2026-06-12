---
title: "Customizing casper on LiveCD - anna reports bad md5sum"
date: 2005-11-15
forum: General Help
---

### Post by diotalevi on 2005-11-15
I'm creating a customized LiveCD but am having issues getting anna to load the rest of the installer from my USB stick. anna complains of a "bad md5sum" while loading the "rest of the installer" - that is, I assume while loading things under the ./pool directory. I've modified the casper deb and I suspect I need to update a checksum someplace.

My ./md5sum.txt is correct - are there other md5sums I need to be checking? Perhaps internal to the debs? Internal to the initrd?

---

### Post by diotalevi on 2005-11-15
I should add - is there a way to get debian-installer or anna to give me more information about what specifically it had a problem with? Right now it gives no information on which thing had a bad md5sum or what its comparing it with. I'm stumped because ./md5sum.txt is correct - it passes the verify command on the same menu.

---

