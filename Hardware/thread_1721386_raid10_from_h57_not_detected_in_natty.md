---
title: "raid10 from h57 not detected in natty"
date: 2011-04-04
forum: Hardware
---

### Post by wbloos on 2011-04-04
I have a PC with onboad raid from an intel h57 chipset.
It supports raid 0,1,5 and 10
I was planning to use raid 10, as it promises to be fast and secure.
Only when i configure a raid10 array, ubuntu 11.04 server beta (64 bit) detects two 'partitions' instead of one raid10 array. Each of these has the size of one of the *four* disks in the array (1TB).
Raid 5 is detected correctly.

Any advise?

edit: the 2 'partitions' carry the name of the raid array i just created. Looks almost as if there is a raid0 partition and a raid1 partition. 
They are numbered 0 and 1, but it has to be a coincidence. It doesn't make sense, because the raid0 should have been 2TB instead of 1TB.

---

### Post by wbloos on 2011-04-04
ok, looks like the 2 'partitions' are two 2-disk raid1 arrays.
The raid0 that comes on top of that might be planned as a software raid in windows by design (only windows drivers are supplied).

So i might choose to create a software raid0 on top of 2 regular raid1 arrays.

---

