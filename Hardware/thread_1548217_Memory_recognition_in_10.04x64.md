---
title: "Memory recognition in 10.04x64"
date: 2010-08-08
forum: Hardware
---

### Post by misteralexander on 2010-08-08
Hello,

I was using 9.04x32 and decided to upgrade my RAM.  I upgraded to 4GB. I then saw that my system didn't recognize all of my RAM, only showing 3.2GB.  I was told, this was because I was using a 32-bit operating system.

Prior to my upgrade in RAM, I made sure to check that my processor (Core2 Duo 1.60Ghz) and chipset (Intel G33 Express) both support my RAM (4GB 4x1GB DDR2 800).

It was recommended that I upgrade to a 64-bit OS.  I installed 10.04x64 tonight, and my system STILL shows 3.2GB of available memory.

I'm confused.  The IRC Ubuntu channel suggested it could be because of my video card, but this being a "Budget Dell" computer, that was seen as unlikely.

Any help in figuring this out, would be GREAT!

-Alex.

---

### Post by cascade9 on 2010-08-08
If you dont have a standalone video card, then some RAM will be used by the video card. From what I can see online, it looks like the G33 can only go to a maximum of 256MB, so it cant explain all the 'missing' 0.8GB, but it explains at least some of it.

---

### Post by slooksterpsv on 2010-08-08
If you open a terminal and run - 
```
uname -a
``` - does it show x86_64 or just x86?

Have you made sure the ram is properly seated? Check and make sure.

If all looks good, I would check BIOS and see if it recognizes 4GB.

---

