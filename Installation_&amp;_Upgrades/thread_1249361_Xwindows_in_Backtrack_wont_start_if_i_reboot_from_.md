---
title: "Xwindows in Backtrack wont start if i reboot from ubuntu"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by jbanjeet on 2009-08-25
**OS installed**
Vista, ubuntu 9.04, backtrack4

Ubuntu and bancktrack use the _same swap partition_


If I power on my computer, I have to problem loading backtrack

However if i restart the computer from ubuntu and then choose backtrack from Grub ...

I can use the command prompt on backtrack with no problem

but when I start Xwindows .... I just see a grey screen and the X pointer and then nothing happens ....


Is it because ubuntu and backtrack are using the same swap partition?


Any help will be appreciated


Thanks

---

### Post by lemming465 on 2009-08-26
No, this problem is probably because your video chip is a little buggy, and it's doing different initializations for warm and cold boots.  Try a BIOS update, if one is available.

Happy 18th birthday to Linux!

---

