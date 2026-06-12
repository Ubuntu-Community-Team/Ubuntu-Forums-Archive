---
title: "NTFS mounting - dolphin"
date: 2008-07-15
forum: Hardware
---

### Post by Quintasan on 2008-07-15
Hi!
I have problems with mounting NTFS partitions using dolphin, it asks me for password and seems to be mounting, but the progress bar is at 0%.
Here's line that I found in dmesg:
```
[  970.154863] NTFS-fs error (device sdb1): parse_options(): Unrecognized mount option locale.
[ 1098.699134] NTFS-fs warning (device sdb1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.

```

I was able to mount it by using mount.ntfs-3g in terminal, but its going to be trouble some

---

### Post by SuperSonic4 on 2008-07-16
Try looking for a package called "NTFS configuration tool" which lets you set your drives to mount automatically

---

### Post by Mark Phelps on 2008-07-16
This is happening because the "locale" option being provided.  

To determine the proper option, do a "locale -a" from a terminal and select the one you want.  You will see they are organized by country.  

For example, I use "en_US.utf8" -- but yours might be different.

---

