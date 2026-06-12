---
title: "Removing File with special characters"
date: 2008-09-21
forum: General Help
---

### Post by lamagra on 2008-09-21
I have a file with an owner of root on my server with special characters.

The name of the file is ?a?J?a???etc...

Anyone know a cheap and easy way to remove said file?


thanks,
Lammy

---

### Post by Zuuted on 2008-09-21
The simple way is "rm ?a?J?a???etc", but you may have to use the following...

```
sudo su
rm -f ?a?J?a???etc
```

if that doesn't work, you must login as root.


Just make sure this is not a required file (or link).
USE CAUTION!


Alternate route... login as root into your GUI desktop, find the file, and delete manually. then reboot.

---

### Post by niteshifter on 2008-09-21
Hi,

Quoteing or escaping:

Quoting: 
```
rm -f "?a?J?a???etc"
```

Escaping:
```
rm -f \?a\?J\?a\?\?\?etc
```

---

### Post by IcemanV9 on 2008-09-21
And, if all fails ...

```
rm -f \?a\?J\?a\?\?\?etc\.\.\.
```

---

### Post by ghostdog74 on 2008-09-21
> **lamagra said:**
> I have a file with an owner of root on my server with special characters.

The name of the file is ?a?J?a???etc...

Anyone know a cheap and easy way to remove said file?


thanks,
Lammy

you can also try using the script in my sig called File Renamer.
eg usage
```

 
# ls -l \?*
-rw-r--r-- 1 root root 0 Sep 21 20:25 ?a?J?a???etc

# ./filerenamer.py -Z "[?]+"  -l "*etc" #use -l to list only
==>>>>  [ /home/?a?J?a???etc ]==>[ None ]

# filerenamer.py -Z "[?]+"  "*etc" #remove -l  to commit
Deleting  /home/?a?J?a???etc

# ls -l \?*
/bin/ls: ?*: No such file or directory



```

---

