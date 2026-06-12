---
title: "Corrupted file system - reinstall ?"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by ddalley on 2009-03-31
It seems my 8.10 install on a hard drive broke down and it is now corrupted. I doubt it will ever boot again, so my question is about how to save recent data in /home.

Can I reinstall Ubuntu and not format the drive, so that I can at least salvage recent unbacked-up data, or does installation force a format of the drive?

If I can do this, then I will reformat the drive after data recovery and reinstall properly with a separate /home directory, but I need to know if this is possible first.

TIA

---

### Post by linuxuser21 on 2009-03-31
If you have the Live CD, you can boot up from that and view the contents on your HDD & do what you need to do with it.

---

### Post by inobe on 2009-03-31
have you been dropped to CLI because of a routine fsck check ?

---

### Post by ddalley on 2009-03-31
Yes, I did a few fsck checks, but it is getting worse with each pass.

I can see one drive from a Live USB, but the Ubuntu drive is not in the device list, so the drive may actually be toast.

---

### Post by inobe on 2009-03-31
get it back in CLI and do

```
fsck -f
```

that will force a full check, you may be faced with a lot of Y/N ?

but obtain your data first.

---

