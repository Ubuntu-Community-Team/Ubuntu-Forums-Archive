---
title: "Mount point suggestions"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by camper365 on 2009-03-29
I have used Ubuntu for a while now, but I have to do a reinstallation (something got corrupted) and I was wondering if I should try to mount different directories under / onto different partitions. I have already had /home under a seperate 10 GB partition, 2 GB Swap, and a 8 GB / partition, but I was wondering if I should mount /boot /var /usr /usr/local /tmp /srv or /opt onto different partitions.
What are the advanteges of doing so, and how should I split them up over a 40 GB hard drive with Windows taking up 10 GB (so basically 30 GB to work with). I want a 10 GB /home partition at least

---

### Post by Pumalite on 2009-03-29
8 GB for '/'
10 GB for '/home'
2 GB for '/swap'
That's plenty.

---

### Post by ronparent on 2009-03-29
Just a simple question for my own information. A reinstall will overwrite your exiswting file system on the install partition. Is /home on a separate safe? Or should personal info be backed up prior to proceeding?

---

### Post by Pumalite on 2009-03-29
If you have a separate /home; keep it. You can do that by Installing,going 'Manual', picking the partitions. In the case of /home; give it mount point '/home, but DO NOT FORMAT IT. Having said that; you should always backup everything when doing a new installation.

---

