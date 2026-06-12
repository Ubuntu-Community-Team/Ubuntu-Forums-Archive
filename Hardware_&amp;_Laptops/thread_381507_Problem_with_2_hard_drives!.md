---
title: "Problem with 2 hard drives!"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by rjop455 on 2007-03-11
I installed linux on one and I can access it. (Duh) But I have another hard drive that I just installed that has just raw data, no OS. They are both the same kind of hard drives. What can I do?

---

### Post by taurus on 2007-03-11
Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by rjop455 on 2007-03-11
Then how do I look/move files on it?

---

### Post by rjop455 on 2007-03-11
When I tpye that I get this:

```

Disk /dev/hdb: 27.3 GB, 27373731840 bytes
255 heads, 63 sectors/track, 3328 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3188    25607578+  83  Linux
/dev/hdb2            3189        3328     1124550    5  Extended
/dev/hdb5            3189        3328     1124518+  82  Linux swap / Solaris

```

And whenever I type in the command it says: Permission denied

---

### Post by rjop455 on 2007-03-11
Anyone? I really need the files on that disk.

---

