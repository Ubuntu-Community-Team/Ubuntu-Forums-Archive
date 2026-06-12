---
title: "split drives from RAID1 array"
date: 2009-02-28
forum: Hardware
---

### Post by lordharsha on 2009-02-28
I've got a server with a RAID1 setup, with two disks. I just found out that you can't move a RAID array to another machine with a different controller. Given that, can I access one of the disks from the array by mounting it as a normal drive on a different machine (without a RAID controller)?

---

### Post by cariboo on 2009-02-28
If you don't have any data corruption issues you should be able to break apart your array and use a single disk on your computer.

Jim

---

