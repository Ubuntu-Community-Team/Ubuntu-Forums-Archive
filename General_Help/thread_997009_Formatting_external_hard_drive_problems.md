---
title: "Formatting external hard drive problems"
date: 2008-11-29
forum: General Help
---

### Post by zotrik on 2008-11-29
Hi everyone,

Here's a specific question for you. I have an external hard drive that is formatted in Mac OSX extended (journaled) format. I'm trying to reformat it in NTFS of FAT32 just to make it compatible with Linux, Windows and Mac OSX. I tried to format it with gparted, but it says that I can't because the format is not recognized. I attached the error message.

Is there any way to format this drive with Ubuntu?

Thanks!!

---

### Post by taurus on 2008-11-29
Is /dev/sdc5 currently mounted?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by zotrik on 2008-11-29
yes it is...

---

### Post by zotrik on 2008-11-29
Great I unmounted it and it works thanks a lot!!!

---

