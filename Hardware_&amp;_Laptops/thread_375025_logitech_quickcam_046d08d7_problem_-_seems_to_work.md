---
title: "logitech quickcam 046d:08d7 problem - seems to work in edgy but not dapper"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by duojet on 2007-03-03
My wife wants to use skype.
I buy a webcam, because she says skype works with linux.
I fight with the webcam.
I insert different distro disks hoping one is plug n play
While using ubuntu edgy I find this post:

[http://ubuntuforums.org/showthread.php?t=344911&highlight=046d%3A08d7](http://ubuntuforums.org/showthread.php?t=344911&highlight=046d%3A08d7)

works like a charm. 
I go back to my old kubuntu dapper install,
seems to work.

problem solved, right? WRONG!
linux skype is voice only, so I'm forced to dual boot. 
After reinstalling kubuntu dapper, the same method no longer works.
The makefile says it's looking for lib/modules/****/build, but it doesn't exist. I tried just making that folder, but it didn't work either, and forcing through the rest of the steps just tells me that gspca.ko is missing.

here's the interesting part:
My old kubuntu install wouldn't actually halt the system at shutdown. Ubuntu edgy won't halt the system either, but my fresh dapper install will.

So, computer WON'T turn off = Camera works
      computer WILL turn off = Camera broken

P.S. I never DELETED the old install, I just have a bunch of spare hard drives around, so I installed on a different one.

---

