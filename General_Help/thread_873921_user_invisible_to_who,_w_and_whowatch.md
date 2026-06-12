---
title: "user invisible to who, w and whowatch?"
date: 2008-07-29
forum: General Help
---

### Post by grischa on 2008-07-29
Hello.
A user is logged in to my ubuntu hardy heron system using sftp. I can see the user through ps and top, but it isn't listed in one of the who utils who, w and whowatch. It doesn't matter if I start these tools as root or admin. The user stays invisible.

It should be a regular user. What might be the reason for this?

---

### Post by caljohnsmith on 2008-07-29
FTP users are not shown as being logged in because you have to actually login to a shell for "who", "w", etc. to see the user. If the remote user were to login via telnet for example, you would see them with "who" and "w".

---

