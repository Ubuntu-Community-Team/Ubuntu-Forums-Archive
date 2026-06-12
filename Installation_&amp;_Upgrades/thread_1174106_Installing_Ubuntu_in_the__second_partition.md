---
title: "Installing Ubuntu in the  second partition"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by moe19790 on 2009-05-30
i have windows vista installed on my computer and the files system used is NTFS, i have 3 partitions C,D & E. When i try to install them Side by side for some reasons it resize my C drive! how can i made it choose the D drive please?

---

### Post by merlinus on 2009-05-30
ubuntu does not use lettered drives, it uses partitions.  Some good info here:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by moe19790 on 2009-05-30
Thanks, that was great link and even provided an extra info which is useful as well. one last question if i used the method, will it be as good, fast and clean as the standard fresh install?

---

### Post by merlinus on 2009-05-30
I don't see why not.  But as a disclaimer, I have never used wubi.  I have always installed directly from a downloaded and burned .iso.

---

### Post by ajgreeny on 2009-05-30
Not quite as quick, if what I have read elsewhere is correct.

Just out of interest, are your D and E partitions(drives) the same size as C in your windows install, and is one of them empty, or can it be emptied by moving files to another?  If you have an empty D or E partition which is a large enough size to use for Ubuntu, I would suggest that you install to that and get the full effect of a Ubuntu install.

If you decide to do it this way, move any files on that partition another using windows, so you have an empty partition, and then go to disk management and delete that partition.  This will make it easier to be sure you get the correct one at the install stage.  Now boot the Ubuntu live CD and when you get to the desktop choose to install.  At the partitioning stage of that choose manual, and you should then see your empty partition as free space and will be able to install to that very easily.

---

### Post by moe19790 on 2009-05-30
i believe the only answer to that is by trying ;) but thank you very much for your help :)

---

### Post by moe19790 on 2009-05-30
Ahaaa, del the partition.... Maybe that what i was missing! Will try that:) thanks for the great tip :)

---

