---
title: "[SOLVED] force user log off in terminal"
date: 2008-07-31
forum: General Help
---

### Post by Potatoj316 on 2008-07-31
I would like to be able to log off a user while I am logged in as someone else.  I am running ubuntu-server and therefore do not have X running.  I have only found answers to this that are basically kill X, or shutdown the other user's instance of X.  I need a way to do this in the terminal that does not invlove X, or gnome, or anything graphical.

---

### Post by geirha on 2008-07-31
The command **w** will list all currently logged in users, and which tty they are logged in at.

The following will show all processes currently running on tty1. Find the pid of the login-process (marked with red) and kill it.
```
$ ps -ef | grep tty1
root      [COLOR="Red"]6248[/COLOR]     1  0 13:12 tty1     00:00:00 /bin/login --       
geirha   19248  6248  0 22:21 tty1     00:00:00 -bash
geirha   19325 19248  0 22:22 tty1     00:00:00 man man
geirha   19337 19325  0 22:22 tty1     00:00:00 pager -s
geirha   19443 19208  0 22:27 pts/1    00:00:00 grep tty1
$ sudo kill 6248
$ ps -ef | grep tty1
root     19470     1  0 22:29 tty1     00:00:00 /sbin/getty 38400 tty1
geirha   19473 19208  0 22:29 pts/1    00:00:00 grep tty1

```

---

### Post by bodhi.zazen on 2008-07-31
[http://www.cyberciti.biz/tips/howto-linux-kill-and-logout-users.html](http://www.cyberciti.biz/tips/howto-linux-kill-and-logout-users.html)

---

### Post by geirha on 2008-08-01
Thanks for the link, haven't heard of skill before. It certainly seems like the right command for the job :)

---

