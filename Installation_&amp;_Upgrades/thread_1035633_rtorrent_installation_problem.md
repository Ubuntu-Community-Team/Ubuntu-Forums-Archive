---
title: "rtorrent installation problem?"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by jestinjoy on 2009-01-09
I tried installing rtorrent. But when I run it ........i get the following error message

```
jestinjoy@jestinjoy-desktop:~$ rtorrent 
rtorrent: Error in option file: ~/.rtorrent.rc:16: Invalid start of name.

```

Please help

---

### Post by devdeblib on 2009-01-09
Have you tried searching your hdd for the string "rtorrent"? 
You should be able to invoke it from where you find it....

if not

TRY THIS IN TERMINAL:

sudo apt-cache search torrent

---

### Post by konsole on 2009-01-10
> **jestinjoy said:**
> ```
jestinjoy@jestinjoy-desktop:~$ rtorrent 
rtorrent: Error in option file: ~/.rtorrent.rc:16: Invalid start of name.

```

rtorrent is telling you that you have a problem at line 16 of your ~/.rtorrent.rc file.

View that file and fix it. Post back here if you can't.

---

