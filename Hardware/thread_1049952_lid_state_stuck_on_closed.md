---
title: "lid state stuck on closed?"
date: 2009-01-25
forum: Hardware
---

### Post by it.henrik on 2009-01-25
Hi all,

Im having a Amilo M1425 and having strange problems with suspend on lid close.

First time I close the lid it does what I set it to do in the power manager, eg suspend on lid close.

Problem is that when I open it I have to press the power button to resume and now the lid state is stuck on closed.

```
$ cat /proc/acpi/button/lid/*/state
state:      closed
```

I have fond a couple of bug reports on similar problems like "missing lid-open resume events" but no solution?

How can I get my laptop to resume on opening the lid or what can I do for a work around?

---

