---
title: "How to create multi RAR archives in Ubuntu?"
date: 2008-10-20
forum: General Help
---

### Post by K.Morgan on 2008-10-20
I have a 20GB folder that i would like to compress into RAR format across five 4GB files.  I have installed RAR in Ubuntu by sudo apt-get install rar but now i'm lost.

---

### Post by oldos2er on 2008-10-20
You can use Archive Manager to create RAR files; I think it's under the menu Applications, Accessories. Or type "file-roller" in a terminal to start the program.

---

### Post by K.Morgan on 2008-10-20
Thanks.  Is there a way of splitting the archives into 4GB pieces? i can't seem to find any options in Archive manager to do this.

---

### Post by Slim Odds on 2008-10-20
> **K.Morgan said:**
> Thanks.  Is there a way of splitting the archives into 4GB pieces? i can't seem to find any options in Archive manager to do this.

info split

the split utility is very handy.

---

### Post by K.Morgan on 2008-10-20
'Info split' doesn't make any sense to me, do i use this instead of Archive manager?

---

### Post by Ms_Angel_D on 2008-10-20
Don't know if your into WinRar but I got it working easily through wine, which I only use when creating multi-part archives. It shouldn't be to difficult to get going in that manner.

---

### Post by ww711 on 2008-10-20
[http://www.computerhope.com/unix/usplit.htm](http://www.computerhope.com/unix/usplit.htm)

there's an example at the bottom on how to use split.

---

### Post by oldos2er on 2008-10-20
> **K.Morgan said:**
> 'Info split' doesn't make any sense to me, do i use this instead of Archive manager?

 "info split" is a command you would enter into the terminal. It just gives you info about the split command. You'd use "split" on an already created RAR archive.

---

### Post by K.Morgan on 2008-10-20
Ah right, so i create the RAR archive first as one big file, and then use split to split the large RAR file into smaller sizes.

---

### Post by qpieus on 2008-10-20
To do exactly what you asked, using only rar:

I don't know how to do it with any GUI, but from the command line it's easy.
Open a terminal and use this command:

```
rar a -r -m3 -v5g archivename path/to/folder/that/you/want/to/split
```

Explanation:

a = add files to archive

r = recursive,     you need this if the folder you want to split has subfolders.

m3 = medium compression,  use 0 for no compression, 5 for best compression. Adjust as desired.

v = multivolume  (split)

5g = 5 GB per volume. Adjust number as desired. Use m for MB for smaller jobs.

archivename = the name you want the archive to be called. If you don't specify a path here, the archive will be placed in whatever directory the terminal is in (probably your /home)

path/to/folder/that/you/want/to/split = self explanatory :)

All this is explained in the rar man page. Rar can do tons of stuff from the command line. In a terminal:```
man rar
```

---

### Post by K.Morgan on 2008-10-21
Thanks qpieus, i almost went down the road of installing Winrar in Wine, been trying so hard not to use any applications in wine, guess now i don't need to.  Great.

---

