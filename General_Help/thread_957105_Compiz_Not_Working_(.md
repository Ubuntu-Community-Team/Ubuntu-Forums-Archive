---
title: "Compiz Not Working :("
date: 2008-10-23
forum: General Help
---

### Post by cafeinoz on 2008-10-23
I use a IBM Think Pad R40e and compiz is installed but not working. When I try to activate the effects in appearance it said effects could not be enabled. When I go to Hardware Drivers it said there are no proprietary drivers in use on this system. Please Help :(.

---

### Post by cafeinoz on 2008-10-23
When I type compiz --replace into the terminal it said:

name@name-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x280a6ec (Ubuntu For)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3e00020 (jeremy@jer)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

---

### Post by Cl0ud9 on 2008-10-23
You need to install the Nvidia or ati driver depending on what type of video card you have. An easy way to do this to to use envyng.
```

sudo apt-get install envyng-core

```
then
```

sudo envyng -t

```
and follow the directions.

---

### Post by eternalnewbee on 2008-10-23
It's quite possible that your graphic card can't handle 3d acceleration. Have the same issue here. Check out this thread. Hopefully you'll have better luck than I did.
[http://ubuntuforums.org/showthread.php?t=948135](http://ubuntuforums.org/showthread.php?t=948135)

---

### Post by overdrank on 2008-10-23
> **cafeinoz said:**
> I use a IBM Think Pad R40e and compiz is installed but not working. When I try to activate the effects in appearance it said effects could not be enabled. When I go to Hardware Drivers it said there are no proprietary drivers in use on this system. Please Help :(.

Hi and you may look at the FAQ's link in my signature as compiz-check may help

Moved to  Desktop Effects & Customization :)

---

