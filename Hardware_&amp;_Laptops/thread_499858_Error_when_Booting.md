---
title: "Error when Booting"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by TheWiseNoob on 2007-07-13
When Ubuntu is loading, about 1/3 the way through I get an error code and it logs in in /vr/log/fsck/checkfs.txt.

Here is the error log:
```
 fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=03fb1d6e-a09e-4cb5-b3ef-403e80f2ae9a'

fsck died with exit status 8 
```

I can still load the GNOME login screen by press Ctrl+Alt+Delete at that error screen though. I found similar threads like [this one]("http://ubuntuforums.org/showthread.php?t=438361&highlight=fsck.ext3") but they were of no help. If anyone has a solution, please tell me.

---

### Post by NilsE on 2007-07-13
Boot from the live cd and run fsck with the fix errors option (man fsck in the terminal will tell you the option) then reboot and see if you get the same error again.

---

