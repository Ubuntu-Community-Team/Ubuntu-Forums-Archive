---
title: "Installing new monitor"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by SteveRwanda on 2006-04-04
I recently installed a version of Ubuntu Breezy badger using one monitor, and it all worked fine. I then tried plugging in a new one (a Sun DP17MO), and found the resolution is on 640x480 and can't be set any higher than that.

Presumably the new monitor is somehow not 'installed' properly, but I can't find any simple option in the menus to do this. 

Any help appreciated, and let me know if there's any essential info I haven't provided,
Steve.

---

### Post by Gustav on 2006-04-04
Just type this in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
and follow the instructions.

---

### Post by henriquemaia on 2006-04-04
[QUOTE=SteveRwanda]I recently installed a version of Ubuntu Breezy badger using one monitor, and it all worked fine. I then tried plugging in a new one (a Sun DP17MO), and found the resolution is on 640x480 and can't be set any higher than that.

Presumably the new monitor is somehow not 'installed' properly, but I can't find any simple option in the menus to do this. 

Any help appreciated, and let me know if there's any essential info I haven't provided,
Steve.[/QUOTE]

Probably you'll have to reconfigure your GUI to work properly with the new monitor at the resolution you want. 

Read this thread and find out more ideas on how to acheive this.

[http://ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate](http://ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate)

---

