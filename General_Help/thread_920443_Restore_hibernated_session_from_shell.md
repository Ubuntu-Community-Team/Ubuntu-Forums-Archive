---
title: "Restore hibernated session from shell?"
date: 2008-09-15
forum: General Help
---

### Post by grazanaut on 2008-09-15
Hi,

I'm wondering if there's a way to restore a hibernated session from a shell.
For example:
- hibernate
- turn back on (but don't login/unlock)
- leave house
- connect in via SSH and restore/unlock the session

First of all, I don't even know which processes to look for to see whether the hibernated session is even sitting there waiting for a password (eg ps aux | grep <???>)...it's the first time I've hibernated a session and I don't even know if it works. And as I've never manually started a gnome-session from a shell, I have no idea what processes are involved.

---

### Post by olejorgen on 2008-09-29
Not completely sure I understand what you want. If the computer is on, but is locked, you can use vnc to unlock it. (maybe gnome-screensaver-command could be useful if you don't want to use vnc)

But this has notthing to do with hibernated sessions so I'm a little confused

---

