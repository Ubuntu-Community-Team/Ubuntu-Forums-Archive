---
title: "libdvdcss"
date: 2005-11-18
forum: General Help
---

### Post by ollieo on 2005-11-18
hello, ollie here, my mate just gave me a copy of ubuntu... i love it, i just been working on getting it set up and so far so gooed, i am currently getting totem to play dvds and it says i need libdvdcss, is there an automated instillation like on synaptic, because i cannot find one. if not is there an apt-get command? any help appreciated... ollie.

---

### Post by aysiu on 2005-11-18
It's no longer in the repositories for legal reasons. Sounds as if you don't live in America, though, so...

Download [this file](ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb) to your desktop. Then type this in the terminal ```
sudo dpkg -i libdvdcss2_1.2.9-0.0_i386.deb
```

---

### Post by ollieo on 2005-11-18
thanks very much very much, is this also all id need to "backup" my current dvd colection?

---

### Post by arnieboy on 2005-11-18
[QUOTE=ollieo]thanks very much very much, is this also all id need to "backup" my current dvd colection?[/QUOTE]
it doesnt back up anything. all it does is enable ur system to play DVD's.

---

### Post by ollieo on 2005-11-18
yes but what do i need to backup my dvds?

---

### Post by arnieboy on 2005-11-18
[QUOTE=ollieo]yes but what do i need to backup my dvds?[/QUOTE]
u mean to rip dvd's and save the files on ur hard disk?

---

### Post by ollieo on 2005-11-18
disk to disk

---

### Post by arnieboy on 2005-11-18
[QUOTE=ollieo]disk to disk[/QUOTE]
do the following from terminal:
sudo apt-get install dvdrip
and then follow the advanced instructions on the following thread:
[http://ubuntuforums.org/showthread.php?t=89851](http://ubuntuforums.org/showthread.php?t=89851)

---

