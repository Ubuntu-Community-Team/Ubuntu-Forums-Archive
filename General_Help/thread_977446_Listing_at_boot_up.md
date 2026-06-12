---
title: "Listing at boot up"
date: 2008-11-10
forum: General Help
---

### Post by gilloz on 2008-11-10
Occasionally at boot up, I get a listing of items that are being checked and it pauses on an item saying that my hard drive has been mounted 37 times and it appears to be checking it out.  Where can I get a complete listing of this process, considering how fast it scans down without reading what is going on?  Reason being, I believe I saw a RED Fail on one item, but it went through so fast I could not read it.

---

### Post by Peter09 on 2008-11-10
the terminal command

```
dmesg | more
```

will allow you to look at the boot log

or System->Admin->System Log

---

### Post by Kevbert on 2008-11-10
If you go to /var/log and take a look at the logs there's a good chance that one of these has the error. The two files that you may want to take a look at are dmesg and kern.log.

---

