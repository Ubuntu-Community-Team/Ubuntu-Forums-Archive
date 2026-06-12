---
title: "Ubuntu wants to load a floppy drive where non exists"
date: 2013-10-12
forum: Hardware
---

### Post by arealperson on 2013-10-12
How do I stop Ubuntu 12.10 x64 bit from trying to load a floppy
when I login to my desktop session.

There is not and will never be a floppy disk.

I've tried but it always gives the error.


Thanks,

---

### Post by Yellow Pasque on 2013-10-12
Try blacklisting the floppy kernel module:
```
echo "blacklist floppy" | sudo tee /etc/modprobe.d/blacklistfloppy.conf
sudo depmod -a
```

---

