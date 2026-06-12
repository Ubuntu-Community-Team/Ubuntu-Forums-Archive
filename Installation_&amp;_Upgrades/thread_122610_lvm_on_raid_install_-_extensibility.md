---
title: "lvm on raid install - extensibility?"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by perler on 2006-01-28
hi,

i plan to do an install along those lines: [https://wiki.ubuntu.com/Installation/LVMOnRaid?highlight=%28raid%29]("https://wiki.ubuntu.com/Installation/LVMOnRaid?highlight=%28raid%29").

i wonder, if i need more space, can i simply add another raid (/dev/md1) and add it to an LVM group to extend any of the mount points (/var, /home, /usr etc).

my ultimate dream is the realibilty of all drives raid 5 but to extend it with more raid 5 units without ever coming to the point where i need to soft link stuff from /var/.. to /home/somewhere because i made the /var partition to small..

what's your strategy?

btw, can i extend a raid5 (i.e. /dev/md0 - _not_ /dev/lvm.../) with an additional drive (again: to extend the raid - not the lvm vg)?

PAT

---

