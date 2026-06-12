---
title: "Upgrade Questions"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Bugs318 on 2009-05-05
I am currently running 8.04 (my first ever ubuntu distro) and am pondering upgrading to 9.04 but have a couple of questions.

1) Would it be best to do a clean install rather than upgrading directly (through 8.10, then to 9.04) for orphaned files/junk/buildup on the system or is there no real difference?

2) If I were to do a clean install, are my /home and /usr directories (which have their own partitions) safe to not reformat in the install and when I designate that location as my new home folder will ubuntu incorporate the files already existing there?

3) Finally, if I were to upgrade via the update manager rather than a clean install, will installed software packages require reinstallation as I presume they would upon a clean install?

Thanks in advance for all of your help!

---

### Post by Partyboi2 on 2009-05-06
If you have your /usr and /home on its own partition during a clean install you would choose the manual partition option and reset the mount point for them.
If you upgrade, your software packages that are in the Ubuntu repos,will automatically be upgraded to the newer versions. 
Since you can not jump releases of Ubuntu when upgrading, doing a clean install would cut out the need to upgrade to 8.10 first.

---

