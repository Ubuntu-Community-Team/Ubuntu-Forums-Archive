---
title: "UNinstallation Problem"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by mykeljee on 2009-07-24
I probably should have done some research before jumping into this but what's done is done: So I recently partitioned my hard drive on my Acer Aspire One and installed ubuntu netbook remix, however I decided I'd rather not have it on there. So I used partition magic to remove that particular partition and redistribute the free space. However upon restarting I still got the grub 1.5 loader and because I removed the partition there IS no os to boot into so I get an error. And now I can't boot into my primary os, Windows XP.

---

### Post by fbugnon on 2009-07-25
Well, what happened was that GRUB was installed into the MBR (master boot record), where Windows boot loader used to be.  Now that the Ubuntu isn't there anymore, GRUB can't find the sequence he needs to boot.

There are probably many tools you can use to restore your MBR but I wouldn't know anything to suggest that doesn't need a CD-drive. Maybe a google search can tell you how to do this booting from a USB.

Another option that could solve your problem - probably faster - is simply reinstall Ubuntu (you can put it in a smaller part of your HD, won't hurt) and dual-boot W and U from there - you might like Ubuntu after all :-)  at least I hope so!

---

### Post by stlsaint on 2009-07-25
look up DaRT for windows xp in google...youll have your answer to get back to xp.

---

