---
title: "Permissin denied to access Gmailfs drive"
date: 2008-09-21
forum: General Help
---

### Post by macozz on 2008-09-21
Hi all,
I am trying to use a Gmail account as a remote drive. Follow the tutorials to do so and finally succeed to mount the system. But when I try to access it I get a message "Access was denied".. What I done wrong? Someone have a similar problem?
Thanks all!

---

### Post by emnaki on 2008-10-04
I also are having problems with permissions. I've mounted successfully, but I can't seem to browse the mount, yet I am able to access the files alright as shown below:

```

kchik@kchik-desktop:~/Ken$ mount.gmailfs ~/Ken/gmail.py ~/Ken/gmailfs/
kchik@kchik-desktop:~/Ken$ ls -l
ls: cannot access gmailfs: Invalid argument
total 80
drwxr-xr-x  4 kchik kchik  4096 2008-07-08 20:17 BACKHTML
drwxr-xr-x  2 kchik kchik  4096 2008-08-26 21:17 Doc
drwxr-xr-x  3 kchik kchik  4096 2008-07-27 18:41 download
d?????????  ? ?     ?         ?                ? gmailfs
lrwxrwxrwx  1 kchik kchik    53 2008-10-04 12:05 gmail.py -> /usr/share/pycentral/gmailfs/site-packages/gmailfs.py

kchik@kchik-desktop:~/Ken$ cd gmailfs
kchik@kchik-desktop:~/Ken/gmailfs$ ls
ls: cannot open directory .: Invalid argument
kchik@kchik-desktop:~/Ken/gmailfs$ sudo ls
ls: cannot open directory .: Permission denied
kchik@kchik-desktop:~/Ken/gmailfs$ cat testdoc.txt
testdata
kchik@kchik-desktop:~/Ken/gmailfs$ 
```

Anyone know how to fix this?

---

### Post by FokkerCharlie on 2009-01-31
Emnaki, did you find a fix for this?

Seeing a similar problem here.

Charlie

---

### Post by emnaki on 2009-01-31
Unfortunately I gave up soon after. I now use DropBox:
[http://www.getdropbox.com/]("http://www.getdropbox.com/")
I only needed smallish storage to synchronize my documents and config files so dropbox was the perfect solution for me, but if you need a big storage you will have to look  elsewhere as dropbox only offers 2GB, but the setup is very easy.

---

