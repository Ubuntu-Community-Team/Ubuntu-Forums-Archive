---
title: "Harddrive performance --noatime,nodiratime,relatime"
date: 2008-09-06
forum: General Help
---

### Post by lift28 on 2008-09-06
Stumbling around i ran across adding noatime,nodiratime to your fstab.
Exp: UUID=29500265-e281-40fe-84a5-dad49cda273a / ext3 noatime,nodiratime,relatime,errors=remount-ro 0 1
 i have done this and can see nice improvements with 
```
sudo hdparm -tT /dev/sdb
```
also in some hd movies that did not play all that smooth, now play very nice:)

Will their any negative effects from this?
why is their a performance increase if "relatime" is their?
from what i read i thought relatime is the newer way to do time stamping.
i did not do the write back tweak for reliability, but I could not find anyone say anything negative about noatime,nodiratime.
anyone have any insight for me?
Thanks

---

### Post by ~LoKe on 2008-09-06
No possible damage that I could ever imagine.  Relatively harmless hack.

---

### Post by lift28 on 2008-09-06
i can not believe the hd movie playback differance:)

---

