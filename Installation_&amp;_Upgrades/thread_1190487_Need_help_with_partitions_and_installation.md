---
title: "Need help with partitions and installation"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by otaku3230 on 2009-06-17
I  have a 160 GB seagate HD on external enclosure where i have already created 4 mounted partitions a long time ago (none of them has any OS) which all have datas already. therefore, how do I  install Ubuntu OS on JUST ONE partition without erasing all the other partitions data. The installation method is still confusing to me because it looks like it is asking to me reformat all the partitions if i choose the entire disk 1st option and for 2nd option: specify partitions manually (advance) what should i do if i  just want to have it installed on one partitions out of 4 partitions on my HD

---

### Post by merlinus on 2009-06-18
In general ubuntu needs at least two partitions, one for / and one for /swap.  If all four of your existing partitions are primary, then you will have to do some changing.

IIRC, you can install without swap, but going forward you may wish to create an extended partition so you won't be undermined by the limit.

Also, does the partitioner in manual mode not give you a choice of where to install?

---

### Post by otaku3230 on 2009-06-18
since their is a risk of having your data erased, what i am doing now is installing it on a brand new HD. However,  before i do that, can you please let me know how to create two different partitions in a HD where I can use one to install Ubuntu and the other for windows xp?

---

### Post by merlinus on 2009-06-18
[http://members.iinet.net/~herman546/index.html]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm")

---

