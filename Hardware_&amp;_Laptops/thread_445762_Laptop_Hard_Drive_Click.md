---
title: "Laptop Hard Drive Click"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by krismatth3 on 2007-05-16
On my laptop, Ubuntu seems to be doing some intermittent activity that causes hard drive access, even when "idle".

It drives me nuts! The hard drive "clicks" rather loudly every 15 seconds or so. 

Any ideas?

EDIT:
This happens only intermittently. I have a window open with top watching to see what happens when it clicks.

---

### Post by yey365 on 2007-05-16
A clicking (sometimes described as a ticking) hard disk is usually an early indicator of the hard disk failing.  Most come with 3-5 year warranties at the moment so check to see if you're covered.  Backup your important info to dvd or external media.

---

### Post by krismatth3 on 2007-05-16
Thanks for the warning, but I feel I should clarify: it's not a death click really, just "normal access" - e.g. somethig intermittently accesses the disk. :)

---

### Post by krismatth3 on 2007-05-17
It turned out to be APM. I turned APM off on the drive via:

```
# hdparm -B 255 /dev/hda
```

and it's stopped clicking.

---

### Post by LinuxVictim on 2007-05-23
I have exactly the same problem,
but the posted solution didn't work.

The poor thing still clicks.:(

---

