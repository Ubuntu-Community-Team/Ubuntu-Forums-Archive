---
title: "WUbi Install Failure"
date: 2008-10-10
forum: General Help
---

### Post by scrun on 2008-10-10
Hi,
I've just installed Wubi on winXP but it doesnt work when I reboot I just get a windows boot and I dont get a boot option screen, I'vve tried instaslling WUBi twice but it doesn't work!!!!! so dissapointed

---

### Post by aysiu on 2008-10-10
Press Windows-R and type ```
msconfig
``` and have a look at the boot.ini tab. Is there anything about Ubuntu in there? And is Ubuntu in the list of programs to Add or Remove in the Control Panel?

---

### Post by scrun on 2008-10-11
Yes in BOOT.INI there is the line
C:\wubildr.mbr="Ubuntu"

and Ubuntu in list of installed programs in Control Panel

---

### Post by aysiu on 2008-10-11
Can you try changing the default boot order to boot to Ubuntu... just to make sure it works? And, while you're there, maybe check that the timeout is 30 seconds and not 0?
[http://psychocats.net/ubuntu/wubi#bootorder](http://psychocats.net/ubuntu/wubi#bootorder)

---

### Post by scrun on 2008-10-11
OK, but how do I reset it back to Windows afterwards I don't want to be left unable to boot windows after making changes

---

### Post by aysiu on 2008-10-11
Hm. Good point. Do you have a Ubuntu Desktop CD ("live CD")? And do you know how to mount Windows drives with it?

If so, you should back up the boot.ini file before you make any changes to it, and then you'd be able to use the Ubuntu CD to restore the original boot.ini file.

I would test this backup restore process before even making any changes.

---

### Post by scrun on 2008-10-11
No, Problem is its a brand new NetBook PC so it has no CD/DVD drive and I sure don't want to screw up Windows, can you think why the installation didn't work the first (or second) time, I wonder if its worth trying again once I've applied all Windows updates to the PC, any suggestions will be much appreciated

---

### Post by aysiu on 2008-10-11
It's a netbook. Hm. Maybe the installation failure has something to do with the size of the drive? Or the SSD hard drive? I have no idea. I'm hoping someone more knowledgeable can chime in.

---

### Post by scrun on 2008-10-11
Blimey I hope it's not the Hard Drive its 80gb !!!

---

### Post by ago on 2008-10-12
All looks good from what I can see. If you have an item in boot.ini it should be displayed in the boot menu. Unless you use a custom bootloader setup. If you change the priority and boot into ubuntu first you can revert by editing boot.ini from ubuntu.

---

### Post by scrun on 2008-10-12
The boot loader doesn't show, I just get an normal Windows load on startup!!

---

### Post by ago on 2008-10-13
> **scrun said:**
> The boot loader doesn't show, I just get an normal Windows load on startup!!

That is a windows issue as far as I can see. If you have an entry in boot.ini that should appear in the boot menu. Unless you have a very different setup.

---

### Post by scrun on 2008-10-15
I think the problem must be with the WUBI installer, because isn't it ment to set up the dual boot, it quite obviously isn't installing correctly. shame

---

