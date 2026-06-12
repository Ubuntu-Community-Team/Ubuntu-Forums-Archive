---
title: "Memory Card Reader not working"
date: 2010-03-10
forum: Hardware
---

### Post by karumudi7 on 2010-03-10
I came across a problem in my Ubuntu Karmic, when I inserted a memory card Reader [External] via USB  the card reader was not recognized by Ubuntu.
But the same card reader was working fine in my Win7.

---

### Post by Fafler on 2010-03-10
Open a terminal and type```
tail -f /var/log/messages
``` and then insert the card reader. After you should see some messages about the card reader. If it doesn't make sense to you, post them here.

---

