---
title: "how to make gdm not search for (EE)?"
date: 2010-02-15
forum: Hardware
---

### Post by akos.maroy on 2010-02-15
I wonder how can one make gdm not search for (EE) messages in the X log file? my X startup generates some such messages, but otherwise it starts up fine when I issue startx. but because gdm seems to scan the log file for messages starting with (EE), it things that X didn't start - and instead of just showing the login screen, it displays an error window.

how can I make it more tolerant to the X server startup process? I was looking in /etc/gdm, but didn't find an obvious solution.

alternatively, how to turn off gdm? by now, it's not started using an init.d script, and "man service" doesn't really give a lot of clues. "service --status-all" doesn't even list gdm...

any help is appreciated

(this is all on 10.04)

---

