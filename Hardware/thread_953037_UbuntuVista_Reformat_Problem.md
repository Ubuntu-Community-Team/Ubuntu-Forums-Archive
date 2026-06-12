---
title: "Ubuntu/Vista Reformat Problem"
date: 2008-10-19
forum: Hardware
---

### Post by Junior21 on 2008-10-19
Here's was my set up:
I had vista installed and ubuntu inside vista.

I reformatted and put Vista on again.  When I boot my computer it still asks me if I want to boot Vista or Ubuntu with Ubuntu is no longer on my system.  I have checked my C drive, not there.. Checked my install/uninstall applications and it's not there neither so I know it's not on my hard drive.  How can I remove the nonworking Ubuntu off my system on startup?

---

### Post by cariboo on 2008-10-19
Go here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Download the iso for whatever version of Vista you are running. Boot from the cd to repair your vista installation.

Jim

---

### Post by inigomontoya on 2008-10-19
You should be able to just remove references to ubuntu in your boot.ini.  Start, Run, type "msconfig".  Should be able to change it from there.

---

### Post by caljohnsmith on 2008-10-19
You could just download "[EasyBCD]("http://neosmart.net/dl.php?id=1")", which is a really easy to use program for modifying Vista's boot menu. That should allow you to remove Ubuntu.

---

### Post by Junior21 on 2008-10-19
Thanks given to the three of you.  Problem resolved.

---

### Post by Junior21 on 2008-12-05
Is their an XP Boot loader?

---

### Post by caljohnsmith on 2008-12-05
> **Junior21 said:**
> Is their an XP Boot loader?
What do you mean? What exactly do you want to accomplish? Do you have XP installed now along with Ubuntu? If so, did you install Ubuntu inside XP or did you give Ubuntu its own partition?

---

### Post by Junior21 on 2008-12-06
I have XP on my C drive and USE TO have XP on my D drive. I've deleted XP off my D drive but when I boot up it still asks which copy of XP do I want to run when the D drive really doesn't have the OS anymore.

---

### Post by caljohnsmith on 2008-12-06
> **Junior21 said:**
> I have XP on my C drive and USE TO have XP on my D drive. I've deleted XP off my D drive but when I boot up it still asks which copy of XP do I want to run when the D drive really doesn't have the OS anymore.
Probably then you have an extra entry listed in your XP's C:\boot.ini file for the other XP install on the D drive. To correct it, just follow [these directions]("http://support.microsoft.com/kb/289022") from Microsoft on how to modify your boot.ini file, and if you want help knowing which line to delete, then please post the contents of the boot.ini file.

---

