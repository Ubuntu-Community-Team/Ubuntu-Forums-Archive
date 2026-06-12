---
title: "[SOLVED] thinkpad function and numlock keys"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by gawdin on 2008-03-28
I have an R50e Thinkpad and I am having problems with getting my numlock and some of the other function keys working on Ubuntu. I was wondering if someone knew how to enable these and/or enabling them properly in a virtual machine (I use VirtualBox). I have tried using an external USB numpad but in order to get it to press a button you had to hold it (which would repeat it several times rather than just doing it once) also the external numpad didn't allow combination of ctrl and alt keys with it. I have considered getting a USB keyboard as I have heard that is most likely to work, but until that time if anyone knows of a way to fix this it would be much appreciated. One thought is that there was a keyboard customizer for thinkpads on windows, I didn't know if there was something similar to that for Ubuntu.

thanks

---

### Post by Whiffle on 2008-03-28
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#NumLock](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#NumLock)

---

### Post by gawdin on 2008-03-29
```
xmodmap:  unable to open file /home/user/.Xmodmap for reading
xmodmap: 1 error encountered, aborting.
```

this is the error i get back after

```
$ xmodmap ~/.Xmodmap
``` (of course i am not actually typing in the $, also sudo has been tried and returns same error)

---

### Post by Whiffle on 2008-03-29
Hmmm, do
```

ls -l ~/.Xmodmap

```
Sounds like the permissions on it are wrong (its not readable)

---

### Post by gawdin on 2008-03-29
seems to think there is no such file or directory

---

### Post by gawdin on 2008-03-29
is it possible that I don't have the xmodmap file installed? like it is included in a package that I don't have yet?

---

### Post by gawdin on 2008-03-29
anyone know?

---

### Post by gawdin on 2008-03-31
I really don't like bumping threads but reposting is worse

---

### Post by gawdin on 2008-04-03
ok I found out that you may not always already have the .Xmodmap file already created (which was my case).

to solve this simply do this in the the user directory (/home/user:~$):

```
xmodmap -pke > .Xmodmap
```

---

