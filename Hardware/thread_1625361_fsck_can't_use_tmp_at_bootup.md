---
title: "fsck can't use /tmp at bootup"
date: 2010-11-19
forum: Hardware
---

### Post by theyain on 2010-11-19
My netbook's hdd recently went through some trauma and now has physical damage on it.   To the point that if I were to restart I am not entirely certain I would be able actually read my MBR. Although for the last three or four times it has (although it hangs at POST) booted. 

If I were to restart fsck would detect the physical damage and ask me if I would like to fix it.  However if I were to tell it to fix it, it would give me the error that /tmp is not available.  But if I were to drop to root during boot process and do fsck on the main partition, everything would run just fun.  Except that it wouldn't fix the file system around the physical damage.

  For a while /tmp was giving me a head ache as things that relied on it (vlc for example) would also tell me that tmp is unreachable.   So, is there anything I can do to fix all this?

And remember, the less rebooting I have to do, the better.  As there is a chance I won't fully reboot.

---

### Post by theyain on 2010-11-19
Bump please.

---

