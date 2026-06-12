---
title: "Resize linux partition"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by iMac on 2006-02-11
I currentley have 10gb set aside for a linux partiton. I have 30gb free space on my hard drive, is there a way to mash these two together without loosing any data?

---

### Post by Ocxic on 2006-02-11
yes there is.  Backup all your data just in case, then load GParted from a live cd and resize the partition, should be relitivly safe but backup just in case.

---

### Post by aysiu on 2006-02-12
[QUOTE=iMac]I currentley have 10gb set aside for a linux partiton. I have 30gb free space on my hard drive, is there a way to mash these two together without loosing any data?[/QUOTE] Only if the 30 GB of free space is *after* the 10 GB you're currently using. If the 30 GB is before, you'll have to reformat. Another option is to just use the 30 GB as a data partition that you mount somewhere (say, /data, for example).

---

