---
title: "lzma problem. Can't install nor upgrade anything."
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by Gummi on 2009-06-27
I've had a problem for the last few months. That problem makes it unable for me to install nor upgrade anything. When I try I get this error:

```
dpkg: error processing (insert package name.filext here) (--remove/install/upgrade):
files list file for package `lzma' contains empty filename
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

This is actually quite the bother. I do hope you can help me.

---

### Post by Gummi on 2009-06-27
bump

---

### Post by Gummi on 2009-06-27
I have tried the ```
sudo dpkg --configure -a
``` and to reinstall all packages concerned with 'lzma' without avail.

I really need some help here.

---

### Post by sniperelite on 2010-02-28
I have the same problem with epiphany browser ,empty filename with some error,please help US

---

### Post by sniperelite on 2010-02-28
i have found the solution by seeing this thread --http://ubuntuforums.org/showthread.php?t=227005

i cant move the files but i can delete the files using this command in terminal-- gksudo nautilus

and i works fine afterwards many Thanks to happynix

---

