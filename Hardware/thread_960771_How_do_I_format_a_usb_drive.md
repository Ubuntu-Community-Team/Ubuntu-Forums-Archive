---
title: "How do I format a usb drive?"
date: 2008-10-27
forum: Hardware
---

### Post by the lemming on 2008-10-27
Hello

I have a scandisk USB 8gb drive which I would like to reformat.  Could somebody please describe how I would format this drive?

Cheers

---

### Post by ukera on 2008-10-27
before you do anything i just want to let you know when you reformat you lose any and everything on that drive.  so if your doing anything major, back it  up.

if your in windows, you can just right click my computer and click manage, then in the toolbar to the left hit disk management, then you see the USB drive, right click, reformat.  or format.  if you just got your hard drive, it should already be formatted.  

if your in linux (hopefully).  in order to format a secondary drive you need root access, so depending on weither your computer is using a SATA connection then you can just view all the connected hard drives with:

```
ls /dev/hd
```

if your in SATA then replace the h in "hd" with an s.

---

### Post by the lemming on 2008-10-28
Hello

I am trying to format a usb pen drive which has the U3 Smart Technology which to be truthful is a pain in the ****.

---

### Post by ottobackwards on 2008-10-28
Google uninstall u3 sandisk.

I had a sandisk and could not get rid of the iso partition through "normal" means in windows or ubuntu, but there is a tool available that will remove it.

---

### Post by the lemming on 2008-10-28
I could use a live cd of gParted but isn't there a similar version somewhere in Ubuntu?

---

