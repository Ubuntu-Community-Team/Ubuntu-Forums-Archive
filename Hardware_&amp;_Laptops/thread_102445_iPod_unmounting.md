---
title: "iPod unmounting"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by billd on 2005-12-12
If I have my iPod plugged in, then it gets recognized automatically and an icon for it is placed upon the desktop -- that's good.  However, the iPod always shows "do not disconnect", which is troubling -- it makes me worry that if I disconnect it I'll have to do a full reset on it.   

To try to disconnect it gracefully, I right-click it and choose unmount.  But then I get an unmount error:

> 
"Unable to eject media"
Show more details:
unable to eject. last error: invalid argument.

And the iPod just continues to flash "do not disconnect."

Any ideas?
Many thanks,
Bill

---

### Post by angkor on 2005-12-12
Try sudo eject /path/to/ipod/mountpoint in a terminal

Substitute the last part with your actual mountpoint....probably /dev/sda2 or something like that.

---

### Post by nrwilk on 2005-12-12
Here's another thread which also brings up this issue.

Cross-referencing ROCKS!
hehe

BTW, I can't even get my ipod to mount under breezy at all.

---

### Post by gatorbrit on 2005-12-13
[QUOTE=angkor]Try sudo eject /path/to/ipod/mountpoint in a terminal

Substitute the last part with your actual mountpoint....probably /dev/sda2 or something like that.[/QUOTE]
I was running into the same problem and that works just fine.  Thanks

---

### Post by aysiu on 2005-12-13
I had the same question four months ago:
[http://www.ubuntuforums.org/showthread.php?t=56515](http://www.ubuntuforums.org/showthread.php?t=56515)

---

