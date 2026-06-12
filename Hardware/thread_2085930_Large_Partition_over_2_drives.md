---
title: "Large Partition over 2 drives"
date: 2012-11-19
forum: Hardware
---

### Post by neuman1812 on 2012-11-19
My setup.
Ubuntu 12.04  
OS - 160sata drive

I just added two 250gb IDE drives for extra storage.

Is there a way in ubuntu to merge the two IDE drives into on giant 500gb partition?  Some sort of raid setup maybe?

My MB  does not support Raid over IDE.

---

### Post by dannyboy79 on 2012-11-19
yes, you can use LVM within ubuntu to make the 2 drives appear as 1 500gb volume.

---

### Post by oldfred on 2012-11-19
Just be sure to have a good backup procedure. If either drive fails you lose all your data from both drives.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

---

