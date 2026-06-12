---
title: "importing .reg file"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by siddharth nayal on 2009-06-19
i m trying to import a .reg file into the wine regedit .......
got the message :
Trying to import from a unicode file: this isn't supported yet.
Please use export as Win 9x/NT4 files from native regedit


help me what to do ????

---

### Post by dstew on 2009-06-19
Here is a [forum post]("http://www.autoitscript.com/forum/index.php?showtopic=18859&view=findpost&p=130872") that tells how to convert a .reg file from unicode to ANSI.

---

### Post by cloupsy on 2009-10-02
You can use iconv to convert your .reg file:
```
iconv -f UNICODE -t ANSI_X3.4 unicode.reg -o converted.reg 
```

---

### Post by applejuicekiss on 2009-10-30
> **cloupsy said:**
> You can use iconv to convert your .reg file:
```
iconv -f UNICODE -t ANSI_X3.4 unicode.reg -o converted.reg 
```

thanks cloupsy.  i had hoped that this was the easy and sensible answer, but when i try that i get:

"iconv: illegal input sequence at position 336"

any idea what this means?  from googling, i'm not sure if this means a bug in iconv or what.  i'm using Karmic, so stuff is still not all working the way it used to.  thanks to anyone who has any ideas.

---

