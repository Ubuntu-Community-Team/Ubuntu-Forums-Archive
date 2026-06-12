---
title: "Different permissions for files/dirs"
date: 2005-11-27
forum: General Help
---

### Post by bassMonkey on 2005-11-27
Hi,

I have a huge amount of files organized into directories in different levels. Currently it's all 755 (dirs & files) and what I'd need is 644 for files and 755 for dirs. I tried:

```
chmod 644 `find * -type f`
chmod 755 `find * -type d`
```

but those don't seem to like spaces in file & dirnames so it doesn't work for me... Any suggestions on how to do this? There's about 150 000 files in 10 000 directories so doing it by hand is not an option! :???:

---

### Post by lcg on 2005-11-27
[QUOTE=bassMonkey]Currently it's all 755 (dirs & files) and what I'd need is 644 for files and 755 for dirs.[/QUOTE]
Try this solution: [Changing permissions recursively]("http://www.ubuntuforums.org/showthread.php?p=522974#post522974")

HTH,
Lars

---

### Post by bassMonkey on 2005-11-27
Incredible, it works! :razz: 

Thank You!

---

### Post by lcg on 2005-11-27
> **bassMonkey]Incredible, it works! :razz: [/QUOTE]
I know.  said:**
> Thank You!
You're welcome.

Lars

---

