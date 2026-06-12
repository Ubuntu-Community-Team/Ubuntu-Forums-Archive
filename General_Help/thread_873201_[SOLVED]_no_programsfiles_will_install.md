---
title: "[SOLVED] no programs/files will install"
date: 2008-07-28
forum: General Help
---

### Post by jbraham on 2008-07-28
Every time i try to download updates or a file/program i keep getting this message. 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report"

but every time i try to manually run the program it says i have to have superuser privileges.

i am new to Linux so any help will be much regarded

thanks J

---

### Post by cszikszoy on 2008-07-28
if it's complaining about root privileges, add 'sudo ' to the beginning of the command.

in this case, try:

```
sudo dpkg --configure -a
```

---

### Post by geirha on 2008-07-28
Try ```
sudo dpkg --configure -a
```. When something needs to be run with superuser privileges, you put sudo infront of it.

---

