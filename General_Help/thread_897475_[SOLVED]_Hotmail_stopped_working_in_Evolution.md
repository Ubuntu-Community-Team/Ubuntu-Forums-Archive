---
title: "[SOLVED] Hotmail stopped working in Evolution"
date: 2008-08-22
forum: General Help
---

### Post by Kevbert on 2008-08-22
I'm trying to use Hotmail in Evolution.  The account is over 7 years old and worked fine up to 2 days ago.  I noticed that people are having problems getting Hotmail through Firefox (but for me this still works).  I'm using Hotway and Hotsmtp and as soon as I attempt to send/receive email I get an fetch error, but don't seem to get anything in the logs.
Any help is appreciated.

---

### Post by Kevbert on 2008-08-25
Bump

---

### Post by Kevbert on 2008-08-26
I've resolved the problem.  I don't know how or why but the first line of my /etc/inetd.conf file was commented out???  This must have been done by an update or something... so the line
```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r
```
was not used...

---

