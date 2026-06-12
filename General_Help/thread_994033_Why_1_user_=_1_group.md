---
title: "Why 1 user = 1 group ?"
date: 2008-11-26
forum: General Help
---

### Post by Bslaccko on 2008-11-26
I'm running Xubuntu 8.10 (cleaned 8.04 and installed 8.10) and
I noted something unclear to me,
why is a group created for every new user?

```
ls -l /home
drwxr-xr-x 94 john john  7168 2008-11-26 12:15 john
drwxr-xr-x 37 moe  moe   7168 2008-11-27 07:32 moe

tail -n 2 /etc/passwd
john:x:1001:1000:John Smith:/home/john:/bin/bash
moe:x:1002:1000:Moe :/home/moe:/bin/bash

tail -n 2 /etc/group
john:x:1000:
moe:x:1001:
```

The user john was created during the installation process while
the user moe was created using users and group management tool
from xfce menu -> System (should be /usr/bin/users-admin).

This seems to me a strange way of managing user.
I'm experienced with different UNIX/Linux systems (IRIX, Solaris,
AIX, SUPER-UX, Red Hat, Suse, Mandrake, Debian, Slackware, FreeBSD)
and I never see it. Indeed, the "word" group means 1 or more users!

Why this choice?
Is there a way to avoid this behaviour and switch back to the old way
of using the "users" group by default?
I tried to set USERGROUPS=no in /etc/adduser.conf but nothing change.
Any explanation/hint ?

Thanks!

---

### Post by kanikilu on 2008-11-26
Making that change to /etc/adduser.conf does not affect how the users-admin tool creates users (it still creates a group with the same name).

However, if you create a new user with the [adduser](http://www.debianadmin.com/manpages/user/addusermanpage.htm) command, it does comply with the conf file and puts the new user in the group specified by the USERS_GID variable.

I couldn't find anything in the gconf-editor or anywhere else to change default options for users-admin, but when you create a new user go to the Advanced tab and select a "Main group".

---

### Post by Bslaccko on 2008-11-27
This is not a major issue, it's fairly simple to switch back
to the default "users" group.
What make me curious is why this choice?
Security? Devices permissions? What else?

---

