---
title: "another harddisk not work?"
date: 2011-10-13
forum: Hardware
---

### Post by than naing on 2011-10-13
my ubentu 11.04 install from cd and 2 hdd but only 1 will use,another hdd was dispear.
I am newbie for ubentu.PLEASE HELP somebody?????

---

### Post by varunendra on 2011-10-14
What makes you think that it has been 'disappeared'? Does the second hard drive's partitions not appear in nautilus (the file browser)?

Please open a terminal (ctrl+alt+t), enter the following command and post back its output here:
```
sudo fdisk -lu
```
(note that it is small 'L' in the command, not numeric '1')
It will list all the hard drives and their partitions detected by Ubuntu.

---

