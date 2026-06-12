---
title: "'Screen' issue"
date: 2008-09-16
forum: General Help
---

### Post by prem1er on 2008-09-16
I have a server set up at home that my roomate and I use (sometimes at the same time remotely via ssh).  We are running rtorrent and use Screen to view from the terminal.  If he opens rtorrent with screen and I can see the process running, how do I view the same screen without opening another rtorrent process?  Thanks.

---

### Post by qstraza on 2008-09-16
use ```
screen -x
```
to resume screen session while friend is in screen too.

Use ```
ctrl + a c
``` to open new window inside a screen session.
Use ```
ctrl + a space
``` to move to the next window..

---

### Post by prem1er on 2008-09-16
lol, beautiful thank you.

---

### Post by qstraza on 2008-09-16
> **prem1er said:**
> lol, beautiful thank you.
```
ctrl + a a
``` to go backwards.

you can even protect your screen session with password.
```
ctrl + a :
```
than type ```
password
```
else follows as follows ;)

---

