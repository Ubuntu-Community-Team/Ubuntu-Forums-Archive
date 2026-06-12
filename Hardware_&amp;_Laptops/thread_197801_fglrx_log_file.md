---
title: "fglrx log file?"
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by kreso on 2006-06-16
Where can I find the log file fglrx dumps its output to? I tried /var/log/Xorg.0.log but I found only init logs there.

I'd like to see in a log file when a tv or crt monitor is connected etc.

---

### Post by Aurelias on 2006-06-16
There should be something in /var/log/kern.log, seeing as the fglrx driver is a kernel module.  Not sure if it'll have the info you're looking for, though.

---

### Post by kreso on 2006-06-17
I've checked it all out, nope.

maybe there's a debug option for fglrx? anyone?

---

