---
title: "Pyback CD/DVD backup"
date: 2008-07-28
forum: General Help
---

### Post by bluzit on 2008-07-28
Using Hardy and can't get this program to access my dvd/cdr drive. I can play cd's and view discs but it won't play nice with this backup app. It's a sata drive, maybe that is the problem. I can't find another program similiar to this so I guess I'm out of luck. Any suggestions I would truly appreciate. Thanks, bluzit:guitar:

---

### Post by DagMan on 2008-07-29
It could be an issue that you can read the device, but don't have write permission.  You can test this by running it as root or with sudo and seeing if it works.  If it does then it's probably a matter of setting yourself to the right group, or fixing the rules that are used to make the device node if it the group can't write... or if you're lazy like me, just creating a startup script that changes the file permissions on every boot.

---

### Post by bluzit on 2008-07-29
Thank you,
Will try your suggestions.  :guitar:

---

