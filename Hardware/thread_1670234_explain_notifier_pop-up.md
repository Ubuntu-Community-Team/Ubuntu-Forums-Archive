---
title: "explain notifier pop-up"
date: 2011-01-18
forum: Hardware
---

### Post by SaintDanBert on 2011-01-18
I've started getting a notifier pop-up -- one of those boxes at the top right of the desktop. The messages says something like, [indent]*Your battery may be broken. It has less that xxx% capacity ...*[/indent]I do not find anything, anywhere on my file system that configures this message.

I thought that I could locate the details using
```

find /path -name "*" -type f -print -exec egrep "pattern" "{} \; | tee somefile 

```

I've searched with the path of /etc, /usr, /opt, and even / using "battery" and "capacity" and similar patterns without finding anything meaningful. 

These pop-up messages must be configured and stored somewhere.
I've read about power-manager (pm) and acpi config without finding what I seek. [highlight]Can anyone tell me how to track this down?[/highlight]

Frustrated,
~~~ 0;-Dan

---

