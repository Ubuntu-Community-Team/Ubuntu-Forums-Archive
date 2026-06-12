---
title: "Joining .001 multi-part files easily"
date: 2008-09-27
forum: General Help
---

### Post by davidryder on 2008-09-27
[http://freebyte.com/hjsplit](http://freebyte.com/hjsplit)

I spent some time trying to install the Linux version then I thought to try the Windows version via Wine and it worked perfectly. The only file needed from the archive is the .exe. No setup is required. 

This has been a big hassle for me and I thought I should post my solution. :D

---

### Post by jpeddicord on 2008-09-27
Offsite link, moved to GH.

---

### Post by binbash on 2008-09-28
I prefer lxsplit

---

### Post by ju2wheels on 2008-09-28
Hmm... why thats not an elegant solution for joining files at all sir. You have Linux, start thinking Linux and not windows:

Joining files of name.00*:
```

cat file.000 file.001 file.002 > file_joined

```

edit:

and just to complete, in the other direction:
```

split -b 22 k fileToSplit splitFileName

```

---

### Post by davidryder on 2008-09-28
I know there are several ways to do it I just prefer GUI over CLI sometimes and I had a hard time installing the linux version of HJSplit. 

That method however isn't very effecient if there are 100 files. 

```
cat file.[0-9][0-9][0-9] > fileTojoin
```

is a little more efficient.

---

### Post by artik1024 on 2012-01-02
Guys ....

```
cat FILE.mkv.* > FILE.mkv
```

2 or 100000files, it works ...
simply

---

### Post by oldos2er on 2012-01-02
Closed, necromancy.

---

