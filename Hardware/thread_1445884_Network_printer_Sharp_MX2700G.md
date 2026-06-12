---
title: "Network printer Sharp MX2700G"
date: 2010-04-03
forum: Hardware
---

### Post by saiful7 on 2010-04-03
Hello,
I just downloaded and install Ubuntu 9.10 Karmic Koala which was a pleasant experience. Everything was smooth and easily configured (even some of them auto configured).

The problem is with the printer Sharp MX2700G (192.168.1.250). I'm trying to solve this for about a week now and apparently my solving skill kinda suck :)

The printer was detected and added into the list, however it didnt respond to test print. Nothing comes out even though it says printing completed.

Sorry for my grammars I'm trying my best to explain. Please help me to understand the problem and the solution for this issue. Thanks in advance.

---

### Post by IcarusR on 2010-04-03
How is the printer networked ? Attatched to a PC or is it a stand-alone network printer?

Does the error log say anything? if so post it.

```
/var/log/cups/error_log
```

---

### Post by saiful7 on 2010-04-04
Hello IcarusR,
This printer is a stand-alone network printer. Below I paste the error log.

> 

E [05/Apr/2010:08:34:44 +0800] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
W [05/Apr/2010:08:38:15 +0800] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
W [05/Apr/2010:08:40:08 +0800] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
E [05/Apr/2010:08:40:25 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
W [05/Apr/2010:08:41:41 +0800] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect


This is the information from the CUPS 1.4.1

> 
[Sharp-MX-2700G]("http://localhost:631/printers/Sharp-MX-2700G") | Sharp MX-2700G | 192.168.1.250 | Sharp MX-2700G Foomatic/pxlcolor (recommended) | Idle - "Ready to print."

---

### Post by saiful7 on 2010-04-06
up. still looking for solution for this issue.

---

### Post by saiful7 on 2010-04-08
bump thread. anyone have idea? would be really appreciated.

---

### Post by saiful7 on 2010-04-11
bump. any ideas?

---

