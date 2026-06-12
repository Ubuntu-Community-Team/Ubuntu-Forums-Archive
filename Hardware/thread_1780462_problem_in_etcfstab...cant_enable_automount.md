---
title: "problem in /etc/fstab...cant enable automount"
date: 2011-06-12
forum: Hardware
---

### Post by apoorvmunshi on 2011-06-12
i tried to enable auto mounting by editing the /etc/fstab file but the file's entries arent normal....there should be a 'default' value  under the options column which i will relace by auto but its not there.i have taken a screenshot...plz help...its doesnt show other partitions even after mounting them manually. plz help.

---

### Post by mikewhatever on 2011-06-12
There are only two partitions in your fstab, root and swap, and they should automount by default. Furthermore, suppose you had a default in fstab, it would have included the following: defaults = rw, suid, dev, exec, auto, nouser, and async.
For more info, see [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).

---

### Post by Elfy on 2011-06-12
Thread closed. Please do not post duplicates, it dilutes community effort.

---

