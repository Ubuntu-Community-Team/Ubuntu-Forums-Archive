---
title: "Akregator crashes"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by horde on 2009-09-09
After an upgrade to KDE 4.3.1, Akregator crashes upon start with a seg fault 11.  The crash handler says the backtrace isn't useful.  From cli I get

> $ akregator
<unknown program name>(19249)/: Communication problem with  "akregator" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

KCrash: Application 'akregator' crashing...
sock_file=/home/user/.kde/socket-hermes/kdeinit4__0

Anyone else having this problem/can help?

---

### Post by horde on 2009-11-06
Found a workaround on [https://bugs.kde.org/show_bug.cgi?id=116482](https://bugs.kde.org/show_bug.cgi?id=116482)

"It seems that Akregator crashes while accessing the backend corrupt the metakit storage, which causes crashes then at startup. A workaround is to move ~/.kde/share/apps/akregator/Archive/*mk4 somewhere else. That should make Akregator start again, but all archived articles are lost.You can then copy mk4 files back and test which one causes the crash..."

---

