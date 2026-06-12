---
title: "keyboard locks up"
date: 2014-06-21
forum: Hardware
---

### Post by rubinglen-b on 2014-06-21
I am using trusty on my amd-64 based computer.  Occasionally the keyboard will just freeze up and stop working.  I still have mouse when this happens.  What can I do to figure out what's going on?  thx

---

### Post by tgalati4 on 2014-06-22
Find a second keyboard and use that and see if you have the same behavior.  Otherwise look in /var/log/syslog and syslog.1 and see if any errors show up.

Open a terminal:

```
cat /var/log/syslog
grep error /var/log/syslog
```

---

