---
title: "Death by magnetic paperclip dispenser!"
date: 2011-07-10
forum: Hardware
---

### Post by Colorado Newb on 2011-07-10
Is it possible that I erased my entire hard drive by leaving my computer running next to a magnetic paperclip dispenser?  I found the screen saver frozen and when I tried to restart I got a GRUB error 2 message.  When I tried to reinstall GRUB from my live disc it couldn't find my hard drive to mount.  When I tried to partition my hard drive it found no operating systems on it.  Did I kill my computer with a paperclip dispenser?

---

### Post by Colorado Newb on 2011-07-10
Is it possible that I erased my entire hard drive by leaving my computer running next to a magnetic paperclip dispenser?  I found the screen saver frozen and when I tried to restart I got a GRUB error 2 message.  When I tried to reinstall GRUB from my live disc it couldn't find my hard drive to mount.  When I tried to partition my hard drive it found no operating systems on it.  Did I kill my computer with a paperclip dispenser?

---

### Post by charliewhizbeez on 2011-07-10
Judging from what you've said, it's quite possible.

---

### Post by coffeecat on 2011-07-10
Possible, or it could be that coincidentally the hard drive is failing, and bad sectors had accumulated enough for the things you describe to appear at the same time. 

Suggest:

Boot into the live CD and open Disk Utility. Check the SMART data on your internal hard drive. Also, in the live session, go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script. What you've posted doesn't sound good, but the boot script will give you a more detailed overview of your system, partitions, and so on. If you want help interpreting the output, post the contents of the RESULTS.txt file.

---

### Post by s.fox on 2011-07-10
Duplicate threads merged.

---

