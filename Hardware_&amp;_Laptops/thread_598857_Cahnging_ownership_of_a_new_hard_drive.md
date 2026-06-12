---
title: "Cahnging ownership of a new hard drive"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by gewitty on 2007-10-31
I just installed a second hard drive, which appears as hdb1. I formatted (ext3) and partitioned it OK, but cannot write to it as it is currently owned by root. Can someone tell me how to change the ownership/permissions so that I can access it from my own user name?

---

### Post by taurus on 2007-10-31
Where do you mount that new harddrive, /dev/hdb1?  _Assuming_ you've mounted it to /media/hdb1 and your login name is **gewitty**, do

```
sudo chown -R** gewitty**:**gewitty** /media/hdb1
ls -la /media
```

---

### Post by gewitty on 2007-10-31
That did the trick. Many thanks.

---

