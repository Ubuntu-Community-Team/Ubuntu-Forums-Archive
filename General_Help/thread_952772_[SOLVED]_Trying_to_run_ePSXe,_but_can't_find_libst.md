---
title: "[SOLVED] Trying to run ePSXe, but can't find libstdc++-libc6.2-2.so.3"
date: 2008-10-19
forum: General Help
---

### Post by RonB123123 on 2008-10-19
I'm trying to run ePSXe, but it can't find libstdc++-libc6.2-2.so.3. ePSXe runs fine, but when I try to configure the video or the sound, it displays this error message.

> 
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory


---

### Post by RonB123123 on 2008-10-19
Nevermind, I found the library. It was supposed to be in the Ubuntu repositories, since it wasn't, I found it by googling it.

In case anyone else has the same problem, go to this page to download it.
[http://packages.debian.org/stable/libs/libstdc++2.10-glibc2.2](http://packages.debian.org/stable/libs/libstdc++2.10-glibc2.2)

---

### Post by Fixman on 2008-10-19
You can anyway open a terminal and write

```

sudo aptitude install build-essential

```

To install this and other related packages (that might cause you similar errors)

---

### Post by GSF1200S on 2008-10-19
I highly recommend pSX- i never could get ePSXe to work... I have pSX version 1.13 if you cant find it anywhere...

---

### Post by alexandrius on 2010-01-22
I decided to run pSX with wine and it works very well, no need to install libraries which are not included in Karmic Koala

---

### Post by Saiko Berry on 2010-01-22
Or you can run pSX with Linux. ._. Since it runs without Wine.

---

