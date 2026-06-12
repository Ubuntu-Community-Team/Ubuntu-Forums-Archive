---
title: "Converting filenames from UTF8 to ISO-8859-1"
date: 2005-11-20
forum: General Help
---

### Post by darkfame on 2005-11-20
Hi,

A long time ago I converted all the filenames on a ext3 partition to UTF8... recently I removed the old linux distro and installed Ubuntu 5.10 on the box.
Now I want to convert the filenames from UTF8 to ISO-8859-1 but I have forgot which tool I used to perform this convertion. Any ideas/suggestions?

---

### Post by hokim on 2005-11-20
mv [filename]  `ls [filename] | iconv -f UTF-8 -t ISO-8859-1`

---

### Post by adamkane on 2006-03-05
convmv Nautilus script:
[http://www.ubuntuforums.org/showthread.php?t=139154](http://www.ubuntuforums.org/showthread.php?t=139154)

---

