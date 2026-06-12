---
title: "Volume groups missing after reboot"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by daudag on 2009-02-13
Hi,

Version: 8.10
Problem: lvm


I need to do vgchange -a y after each start, before I can mount any LV.

Entry ds-mod in /etc/modules exists

How may I start vgchange -a y during boot or other ways to solve this problem requested.

Thanks

---

### Post by lemming465 on 2009-02-14
There is probably a better way, but a brute force kludge that might work would be to edit it into the beginning of the do_start() function in /etc/init.d/mountall.sh.

---

### Post by m00dawg on 2009-06-03
Yep, that changed worked, although I am bummed out that there is no real fix yet for this. After over an hour of searching, this has been the best solution, which makes me think there's a bug running around in regards to this...

---

