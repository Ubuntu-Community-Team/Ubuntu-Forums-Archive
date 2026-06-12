---
title: "Evolution Backup"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by noeluylee on 2005-12-21
Hi,

I want to backup my Novell Evolution Datas, including addressbook, calendars and mails. I want to backup for security purposes :) 

What are the best way of backing up those datas?

I tried to copy .evolutions and .gconf/apps/evolution, but I failed on .evolution/addressbook/views, all file on it, with file name current_view-file:___home_noel_.evolution_addressbook_local_1132063429.10623.2@NOEL-Linux.xml

Hope you could help. :)


Noel

---

### Post by aysiu on 2005-12-21
Are you trying to copy using the command line? If so, you may have to do a ```
cp -r
``` instead of just ```
cp
```

The only other thing I can think of is that you may have to *close* Evolution before even copying the config files.

---

### Post by GrammatonCleric on 2005-12-21
Personally, I perfer to backup my evolution with tar.

```
tar cz .evolution/ > /some/output/path/evolution-date.tgz
```

GC

---

