---
title: "[SOLVED] Missing Library -lbz2"
date: 2008-07-17
forum: General Help
---

### Post by xanders on 2008-07-17
Hi all Guys,

 I'm having a situation trying to compile a source when jam is linking all the objects files is looking for a Library "-lbz2" if anyone had this situation before and know how to fix it please send a solution or comments about it.

```
Link ProjectName 
/usr/bin/ld: cannot find -lbz2
collect2: ld returned 1 exit status

```

Thanks to All

---

### Post by geraldm on 2008-07-17
It is in the source package bzip2.
I did not check, but I would expect that it is available also as a library package.

Gerald

---

### Post by jimv on 2008-07-18
I *think* it wants libbz2.

sudo apt-get install libbz2

---

### Post by xanders on 2008-07-19
> **jimv said:**
> I *think* it wants libbz2.

sudo apt-get install libbz2

Yes it was that one.

Thanks

---

### Post by blackzafiro on 2009-05-21
I had the same problem, but I required
```
sudo apt-get install libbz2-dev
```

---

### Post by ariismail on 2010-03-03
I also had the same problem while building Opencv and resolved it by:

```
sudo apt-get install libbz2-dev
```

---

### Post by oxana on 2011-11-23
Hi, guys!
Thanks for your advice.

---

### Post by nothingspecial on 2011-11-23
Please do not bump old threads to the top.

Closed.

---

