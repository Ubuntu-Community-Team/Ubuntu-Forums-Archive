---
title: "/var/cache/apt/archives"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by potzdonner on 2009-04-21
Hi all

in /var/cache/apt/archives are stored a lot of huge gz-files. Because I'm running short of disk memory a have a question: Are these files really needed for running ubuntu or can I backup these files and then delete them temporarly?

---

### Post by StuartN on 2009-04-21
apt-get autoremove or apt-get autoclean or apt-get clean will clear out automatic depepndency files, redundant files or all files from the package cache. They have already been applied and are, in any case, still available in the repositories, so it makes no difference to your installation to clear them out.

---

### Post by potzdonner on 2009-04-22
> **StuartN said:**
> apt-get autoremove or apt-get autoclean or apt-get clean will clear out automatic depepndency files, redundant files or all files from the package cache. They have already been applied and are, in any case, still available in the repositories, so it makes no difference to your installation to clear them out.

thx a lot, it worked very well.

---

