---
title: "Restore i386 Backup to AMD?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Modern_Kilroy on 2009-10-30
Is it possible to take a backup of an i386 Karmic to an AMD processor system? I have a buddy who really likes all the tweaks and installs I have done with my installation and it would save a lot of time if we can just install the backup files. The backup was done with a simple tar of the filesystem (complete, including /home), so everything should be included (except proc, lost+found, sys, temp). 
 
Thanks.

---

### Post by mikewhatever on 2009-10-30
It's certainly possible to install using a tar.gz backup, but you might run into problems related to different hardware and different partitions. Be prepared to troubleshoot. I think a better way would be to do a clean installation at your friend's and then use the settings from your home directory.

---

### Post by Modern_Kilroy on 2009-10-30
Thanks. I figure I'll give it the ole college try first, then fall back to reinstall and export my markings and import on his if all esle fails.

---

### Post by mikewhatever on 2009-10-30
You can simply tar.gz your home folder and restore it on your friend's computer. Rsync can do the same.

---

