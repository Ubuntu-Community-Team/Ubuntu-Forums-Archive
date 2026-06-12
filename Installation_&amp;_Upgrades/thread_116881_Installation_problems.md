---
title: "Installation problems"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by jpinzonc on 2006-01-13
Hi everyone
I have installed UBUNTU several times today. I am doing it in a External HDD and we the first boot comes, it said that the /dev/sb1 was not found and drop to the shell. I have tried adding mptbase and mptsscsih to the module, but still don't work. Can any bdoy give me any idea? 
Thanks
Jorge

---

### Post by aysiu on 2006-01-14
Maybe it's not at /dev/sdb1 all the time. Maybe it comes up as /dev/sda1 and is looking for the drive at /dev/sdb1 and thus can't mount it as /

---

