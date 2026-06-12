---
title: "Ubuntu installed on external hard disk"
date: 2011-10-26
forum: Hardware
---

### Post by srihari3000 on 2011-10-26
I had installed Ubuntu on my external hard disk, choosing the option  "use complete disk" for Ubuntu installation. It's installed fine and I'm able to boot from it to use Ubuntu. But when I connect the hard disk to my laptop running windows 7, hard disk is not detected. I can find it in the device manager but I am not able to access it. Plz let me know if there is any way I can access it windows 7.

---

### Post by diasf on 2011-10-26
Check the bios of the laptop to see if there's a usb boot option.

BUT i have to warn you that installing the system on one PC and booting it on another isn't a very smart thing to do. The default ubuntu kernel is generic enough for it to work, but you might encounter some problems with misconfigured hardware that hardly are worth the trouble. You might consider a liveCD if is something sporadic or a "real" installation if you are going to use it more often (20Gb is nothing these days and is more than enough for ubuntu itself....)

---

### Post by srihari3000 on 2011-10-31
There is no problem with booting from the hard disk. The problem is that, when I am using Windows 7 and I connect my external hard disk (just like any other usb drive), The external hard disk is not displayed as a drive, but I can find it in the device manager. Hope I have made the problem clear.

P.S--> The Ubuntu installation was done on the ext hard disk using the same PC on which I am trying to access the ext HD, while using windows 7.

---

### Post by diasf on 2011-10-31
If you used all the drive when installing ubuntu, chances are the whole disc is formatted using ext, windows won't read it easily. All normal so far.

---

