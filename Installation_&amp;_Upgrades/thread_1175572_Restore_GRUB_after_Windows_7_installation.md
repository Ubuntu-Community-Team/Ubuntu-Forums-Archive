---
title: "Restore GRUB after Windows 7 installation"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by blackriven on 2009-06-01
Having installed Windows 7 my Ubuntu partition is now inaccessible. I read somewhere in these forums (can't seem to find the tread at the moment) that restoring GRUB may be problematic with Windows 7. Is that true? If so, how do I go about restoring access to Ubuntu. 

Also I would appreciate some walkthrough regarding restoration of GRUB. 
Thanks in advance.

---

### Post by raymondh on 2009-06-01
Hello BlackRiven,

Hope this helps

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Post back if you need assistance.

Regards,

---

### Post by coffeecat on 2009-06-01
**blackriven**, of all the methods described in the link that **raymondhensen** posted, by far the easiest is to use SuperGrubDisk. However, the link to SGD from that page is not working at the moment. A working link to SGD is:
[LEFT]
[http://www.supergrubdisk.org](http://www.supergrubdisk.org)[/LEFT]

Follow the bit under 'as a standalone CD' in **raymondhensen's** link and you'll have grub restored in no time.

By the way...

> **blackriven said:**
> I read somewhere in these forums (can't seem to find the tread at the moment) that restoring GRUB may be problematic with Windows 7. Is that true?
[LEFT]
Not in the slightest. I'm posting from Windows 7 atm, on a machine on which I successfully restored grub after installing Windows 7. Windows 7 is no different in this respect from 2000, XP and Vista.

Good luck!
[/LEFT]

---

### Post by raymondh on 2009-06-01
> **coffeecat said:**
> **blackriven**, of all the methods described in the link that **raymondhensen** posted, by far the easiest is to use SuperGrubDisk. However, the link to SGD from that page is not working at the moment. A working link to SGD is:
[LEFT]
[http://www.supergrubdisk.org](http://www.supergrubdisk.org)[/LEFT]

Follow the bit under 'as a standalone CD' in **raymondhensen's** link and you'll have grub restored in no time.

By the way...


[LEFT]
Not in the slightest. I'm posting from Windows 7 atm, on a machine on which I successfully restored grub after installing Windows 7. Windows 7 is no different in this respect from 2000, XP and Vista.

Good luck!
[/LEFT]

+1 on supergrubdisk .... that and a disk of gparted are invaluable tools.

ditto on win 7 ... though I am about to uninstall it in a few moments ... but that is for another topic/thread :)

---

### Post by guppydas on 2012-03-28
SuperGrub disk saved my day. For some reason I had to re-install Windows 7 after it behaved erratically. Before that it was working great. I had Grube taking care of booting between Ubuntu and Windows 7. 

SuperGrub dis and GParted are a must to have.

:guitar:

---

