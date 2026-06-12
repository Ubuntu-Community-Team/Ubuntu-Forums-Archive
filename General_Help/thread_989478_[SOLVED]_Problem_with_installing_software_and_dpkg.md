---
title: "[SOLVED] Problem with installing software and dpkg"
date: 2008-11-21
forum: General Help
---

### Post by arturus on 2008-11-21
When I try to install new programs I got a this error
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What should I do?
I had the same problem when I tried to change something in hibernation.

Thanks in advance.

---

### Post by aysiu on 2008-11-21
Close whatever you're using to install the programs, and then paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo dpkg --configure -a
```

---

### Post by fooman on 2008-11-21
open a terminal and type or copy/paste:

```
sudo dpkg --configure -a
```

---

### Post by arturus on 2008-11-21
Cheers. It's so easy:)

---

