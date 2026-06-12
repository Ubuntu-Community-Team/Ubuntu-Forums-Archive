---
title: "xtra drive"
date: 2014-03-28
forum: Hardware
---

### Post by night116 on 2014-03-28
I have a laptop with 3 hard drives
sdc1 227Gb : my / root partition
sdb1 917Gb : my /home2 partition
sda1 917Gb : my /home partition

I can access my /home partition with no problems, but my second spare /home2 drive shows up in devices computer section, so does /home, but I can not make any directories or folders n my /home2.
can any one help me ?

the /home2 partition has alost and found folder in it and thats all.

---

### Post by night116 on 2014-03-28
dont worry fixed it by reading another post similar
sudo chown -R fred /home2

---

