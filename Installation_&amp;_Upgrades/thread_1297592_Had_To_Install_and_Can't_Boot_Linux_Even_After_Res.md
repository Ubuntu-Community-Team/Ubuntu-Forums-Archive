---
title: "Had To Install and Can't Boot Linux Even After Restoring Grub"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by DocEsq on 2009-10-21
Hi All,

I originally had XP installed on the primary drive and then installed Ubuntu 8.04 onto the second drive using the method described [here](http://ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot+Hard+Drives) by confused57.  All worked well.

XP being what it is I had to a complete reinstall so I disconnected the second hard drive that had Ubuntu on it and proceeded reinstalling XP.

After reinstalling XP I reconnected the second hard drive that had Ubuntu on it (making it the primary boot drive now like before) and using the instructions [ from this site](http://didta.com/2009/08/restore-grub-after-installing-windows/).

I was able to get back my original Grub Boot Menu but when I highlighted and and attempted to boot Windows or any of the Ubuntu Kernal choices (including the sage mode) I kept getting an error.  Disconnecting the second drive and having the BIOS boot to windows drive I was able to get back into XP.

What if anything am I doing wrong and is there a way I get back to dual booting without having to reinstall Ubuntu?

Thanks for any help.

DocEsq

---

### Post by darco on 2009-10-21
I recently dual booted on a 2nd drive, adding Karmic which uses the grub2 menu. After reconnecting the first drive, Grub2 on Karmic picked up the OS's on the first drive. Which makes me think you could install grub2. If too challenging you may just want to read the the full Ubuntu article on reinstalling Ubuntu after installing Windows. Your second link is only a snippet of the original article

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

darco

---

### Post by DocEsq on 2009-10-27
I fixed my issue.  It seems that after I had unplugged the Ubuntu disk so as to reinstall XP.  After that I replugged the Ubuntu disk but I forgot to make it the primary booting disk.  Once I did that all was well (though the XP install seems a bit shaky).

DocEsq

---

