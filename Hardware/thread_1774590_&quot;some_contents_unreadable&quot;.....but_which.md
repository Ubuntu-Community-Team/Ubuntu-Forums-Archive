---
title: "&quot;some contents unreadable&quot;.....but which are they?"
date: 2011-06-03
forum: Hardware
---

### Post by mactece on 2011-06-03
The good news: I just got out from underneath a hard drive crash with almost all my data intact 

The bad news: having backed it up, installed a new hard drive and copied the data back it all appears to be fine but I get the following message when I do a "file properties" on it - "258,840 items, totalling 111.7 GB
(some contents unreadable)"

The question: How can I find out which files are corrupted?

---

### Post by wolfgangmcq on 2011-06-03
All hard drives say that.. it's the files in /dev/ etc. Don't worry about it.

---

### Post by mactece on 2011-06-03
solved it - apparently they are unreadable in the sense that I can't read them, not that the computer can't read them. If I start a nautilus session as root (gksudo nautilus) then the message disappears.

Doh!


More here
[http://ubuntuforums.org/showthread.php?t=1247356](http://ubuntuforums.org/showthread.php?t=1247356)

---

### Post by mactece on 2011-06-03
Thanks for the quick reply wolfgangmcq. much appreciated. I'll mark this as solved now.

---

