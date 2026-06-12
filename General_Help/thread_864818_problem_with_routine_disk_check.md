---
title: "problem with routine disk check"
date: 2008-07-20
forum: General Help
---

### Post by spiritfox on 2008-07-20
When booting, i get the "routine disk check: press esc to skip" message.  It gets up to 12% and drops me to ash and says fsck failed.  When i try to run it manually like it says, it tells me it doesn't know what fsck is.  If i hit exit ubuntu boots normally.  Should I be worried?  I've already backed up everything.

---

### Post by Victormd on 2008-07-27
I don't think you would need to worry about it. Especially since you've backed everything up. On that note, the command should be something like:
```
fsck -p /dev/sda
```
or
```
e2fsck -n /dev/hdXX
```

---

