---
title: "external IDE enclosure -- need drivers??"
date: 2009-12-01
forum: Hardware
---

### Post by oospill on 2009-12-01
I've got a couple 3.5" IDE drives, and would like to hook them up to my laptop, so that I can backup data, and upgrade to Ubuntu 9.10. (I know I need a fresh install) I noticed that all of the external IDE enclosures all come with a driver disk.  I'm 95% sure it has nothing on it for linux.  

do I need drivers, or should it be plug and play?

thanks

---

### Post by cascade9 on 2009-12-01
I've made a few external hard drive boxes, and never needed a driver disc for windows or linux (or BSD for that matter). I spose in very rare occasions windows might actually 'need' a driver disc for an external, but in my experience those discs just have backup and encryption software, sometimes 'bonus' software like antivirus, on them.

---

### Post by oospill on 2009-12-01
excellent.  thank you so much for the post!!

---

### Post by Some Penguin on 2009-12-01
The issue is not the connection between the enclosure and the drive, but between the enclosure and the computer.  If, for instance, the enclosure provides a USB interface and supports the USB Mass Storage standard (which is extremely likely), then your Ubuntu setup will (by default) support it.   You could compile a custom kernel which doesn't, but it is unlikely that you have done so.

The provided software for Microsoft Windows is likely to provide other functionality such as synchronization of files between external drive and your internal hard drives, or for creating backups.  *That* may require some more poking around to find equivalents.

---

### Post by coffeecat on 2009-12-01
If those driver discs don't have the sort of special software that Some Penguin mentions, you'll probably find that they contain the USB driver for Windows 98. Yes, that's right. There are still some people out there using Windows 98. I've met one. :-s

---

### Post by cascade9 on 2009-12-02
opps, yeah, I forget Win98 (and 95 OSR 2.1 as well) needs the USB drivers. Yes, thats normally on those discs, even though almost everyone has flicked off Win9x these days. If your reading this, and you havent- get rid of that dinosaur! Win9x is unsupported these days, get a light linux distro if you want to keep running that old box.....or take it offline, please. :)

---

### Post by coffeecat on 2009-12-02
> **cascade9 said:**
>  get rid of that dinosaur! Win9x is unsupported these days, get a light linux distro if you want to keep running that old box

Don't knock Windows 98. :wink: There are plenty of W98 boxes out there doing sterling work....

..... sending out Viagra emails. :rolleyes:

---

### Post by cascade9 on 2009-12-02
Thereby keeping the internet up eh? ;)

---

