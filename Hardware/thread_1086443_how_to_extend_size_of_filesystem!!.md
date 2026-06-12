---
title: "how to extend size of filesystem!!??"
date: 2009-03-04
forum: Hardware
---

### Post by chinmaya_n on 2009-03-04
My linux / filesystem is 25GB. But now i would like to extend it to 40 GB. Can i do this ?? with out any lose ?? B'se I installed many applications on my system.....If i format it i'll  loose all of them.........!!
Can any one suggest how to increase the size of filesystem with out formatting it ??

---

### Post by agim on 2009-03-04
use gparted.

If you are using gnome, go to System->Administration->Partition Editor.

---

### Post by chinmaya_n on 2009-03-04
How can we join two partitions......can we extend a patition with out any lose of its contents ????

---

### Post by Empirecrzy241 on 2009-03-04
I don't think gparted supports the joining of two partitions without the loss of data.  The only way that I've found to do it would be to delete one partition and extend the other, or to delete both partitions and make one new one covering all of your "unallocated space".

---

### Post by avtolle on 2009-03-04
Be sure to backup; and, you'll want to do your partition managing from a Live CD, whether Gparted, the Ubuntu Live CD, or some other analogous application. You will need to boot from the Live CD, as if you are booted into Ubuntu, the drive will be mounted (in use), and as the partition referenced is the / partition (as I read your post), it cannot be unmounted AFAIK to allow you to work on it with the system running.

---

### Post by chinmaya_n on 2009-09-10
Thanks!! :popcorn:

---

