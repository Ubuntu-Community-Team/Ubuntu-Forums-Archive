---
title: "[SOLVED] Move files but not folders in directory tree to single folder"
date: 2008-08-23
forum: General Help
---

### Post by itix on 2008-08-23
Hi... I'm here again with my wierd requests. I need to move every file that ends with .jpg in my directory tree to a single folder containing jpg's.

I know a way to go on about this in Ubuntu, but as this is Xubuntu, it doesn't have the sofisticated file search. I could of course download the packages myself, but my poor Eee doesn't have much disk space, so I thought of some cool terminal based way. Tried to read *man mv* and *man cp* and did some google-ing but it didn't do me much good.

---

### Post by amitkher on 2008-08-23
testIn is the root of the source directory tree. testOut is the single folder where all jpgs will be moved. If the name of 2 jpg file is the same, you will get only one of them in testOut. Replace cp with mv if you want to remove the files from testIn after being moved to testOut. First try with cp and check all your files are correctly being copied to testOut

```

cp `find testIn/ | grep --color=never '.jpg$'` testOut/

```

---

### Post by itix on 2008-08-23
Would this work with files (or paths for that matter) that has blank spaces in them?
I get a ton of *cp: cannot stat blah blah: no such file or directory* (where 'blah blah' is things like '-', '008' and half filled paths etc.)

---

### Post by ghostdog74 on 2008-08-23
> **amitkher said:**
> 

```

cp `find testIn/ | grep --color=never '.jpg$'` testOut/

```

it will break for files with spaces.

@OP
```

find /path -type f -name "*.jpg" -exec mv "{}" /somewhere \;

```

---

### Post by itix on 2008-08-23
Nice. Worked wonders. Thanx...

EDIT: Might I ask why you need the last '\' ??
I tried something similar that I constructed throgh various google finds, but I didn't have the brackets and the '\'

---

### Post by ghostdog74 on 2008-08-23
check the man page of find and then go to the explanation for -exec. Its stated there. Always check the man page first.

---

