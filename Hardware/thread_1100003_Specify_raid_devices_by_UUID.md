---
title: "Specify raid devices by UUID?"
date: 2009-03-18
forum: Hardware
---

### Post by rhymed on 2009-03-18
I've used mdadm to successfully create a RAID0 array across a few USB flash drives to get better performance from the drives. All is fine with that, and when I specify the devices that are used in the array in the mdadm.conf file I specify the devices by name (ex. /dev/sdb, /dev/sdc, etc). Since these are removable drives, they may not always have the same device name. Does anyone know if it's possible to specify the devices by UUID in the mdadm.conf file. I haven't been able to find any info on it so I suspect it's not possible.

Thanks in advance for the info.

---

### Post by MartinEve on 2009-06-29
I would also be interested if someone had a solution to this...

---

### Post by ronparent on 2009-06-29
This may not be an answer, but, at least a clue. See this thread for an example of a mdadm.conf with uuid's. : [http://ubuntuforums.org/showthread.php?t=1197377](http://ubuntuforums.org/showthread.php?t=1197377)

---

### Post by MartinEve on 2009-06-30
Many thanks for the heads-up - I'll check it out :)

---

