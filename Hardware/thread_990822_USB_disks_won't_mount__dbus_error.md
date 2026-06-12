---
title: "USB disks won't mount / dbus error"
date: 2008-11-23
forum: Hardware
---

### Post by trey333om on 2008-11-23
I've a Dell N-series with an 8.10 upgrade installed. Whenever I try to plug in any USB thumbdrive, it gives me a:

[INDENT][I]Unable to mount UBUNTU-USB

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/I][/INDENT]

Portable hard drives work fine. The same thumbdrives work perfectly in my two other computers.

Tried restarting HAL and DBus, but no help...:
[INDENT]*sudo /etc/init.d/hal restart && sudo /etc/init.d/dbus restart*[/INDENT]

Any ideas?

---

