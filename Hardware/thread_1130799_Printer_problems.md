---
title: "Printer problems"
date: 2009-04-20
forum: Hardware
---

### Post by Dooley on 2009-04-20
Hey all,

Within ubuntu I'm trying to get printing working but to no avail.

When I run
```

lpr file.pdf

```
It just seems to constantly run till doing nothing for ages till eventually I get this error.

lpr: Error - scheduler not responding!

When I access it via gnome's configure printers, it just crashes too.

Accessing cups via localhost:631 I can see that my printer(A Lexmark 3816) is detected. But again, when I try print jobs it just doesn't print anf is constantly processing. I've changed the cups config file back to the /etc/cups/cupsd.conf.default to see if that was the issue but no luck.

I've also tried re-installing cups but still no luck.

Hope someone can help. 

Thanks.
Dooley

---

