---
title: "unrar multiple files with the same password"
date: 2008-11-21
forum: General Help
---

### Post by creta on 2008-11-21
hello there

I would be most grateful if someone could help on how to extract multiple rar files with the same password.

thanks in advance

---

### Post by taurus on 2008-11-21
You can extract the first file and when it asks you for a password, type it in and it will extract the rest of the rar files.

Applications -> Accessories -> Terminal
```
unrar x filename.r00
```

Of course, you need to install unrar first before you can use it.

---

### Post by jasondean on 2008-12-28
I could be mistaken but I think the original poster meant if they were different individual rar files(not the split archives) i.e. Movie.rar and Music.rar both use the same password but u would have to extract them one at a time and re-enter password for each., I have been looking for the same solution.

---

### Post by dstroixr on 2009-03-05
RarMonkey handles this situation nicely. Just enter the password once and check "Use password for all other archives in this operation".

[http://www.rarmonkey.com](http://www.rarmonkey.com)

---

### Post by p3tris on 2009-06-14
create a bash file and put this inside it:

```
#!/bin/sh
#
# unrar/unzip/join all files in directory

for f in *.rar;do unrar -p<password> e $f;done
#for f in *.zip;do unzip -P <password> $f;done
#for f in *.001;do lxsplit -j $f;done
```

Uncomment the command you want and run it in the folder the rars are in.
In the place of <password> put the password (without the <>).
Careful that unrar takes -p and password WITHOUT SPACE BETWEEN THEM. While unzip with space. Hope fits your needs.

---

