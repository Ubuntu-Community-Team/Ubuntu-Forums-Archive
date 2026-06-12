---
title: "Disk error check after cloning (using dd)"
date: 2010-05-19
forum: Hardware
---

### Post by guttdude on 2010-05-19
I thought that I got bad sectors on old hard drive and I'm trying to clone hard drive from the bad one to a new one using dd. I didn't used noerror options. The command is following.

```
dd if=/dev/sda1 bs=64K | dd of=/dev/sdb1 bs=64K
```

The questions are the new hard drive won't have bad sectors, so 

1) how can I know which files were corrupted? Can I use the normal checkdisk on the new disk? 

2) Do I understand correctly that if there is error it would show up? (I know that it would be filled in the new one as null if I use noerror options.) How about this case what dd filled?

---

### Post by guttdude on 2010-05-19
Anyone knows how to verified the cloned disk?

---

