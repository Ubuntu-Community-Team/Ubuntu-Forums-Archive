---
title: "No header files in /usr/include"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by shredder12 on 2009-08-30
I had installed xubuntu a few days ago.. and when I tried to compile a c program I got errors saying that
there were no files or directory by the name of stdio.h, sys/socket.h etc.
when i looked into /usr/include/ directory there were no header files there..

I have updated my system..
Is there anything else I am supposed to do..

---

### Post by Lampi on 2009-08-30
you need to install a few dev packages - let's say you try to compile nautilus, you need to install nautilus dev packages like this:

```
sudo apt-get build-dep nautilus
```

Another way is to check [http://packages.ubuntu.com/](http://packages.ubuntu.com/) - just fill in the header file you need and hit search - it will show you the dev package you need for this header file

---

### Post by sisco311 on 2009-08-30
/usr/include/stdio.h is provided by libc6-dev. try to install the package:
```
sudo apt-get install libc6-dev
```

---

### Post by shredder12 on 2009-08-30
> **sisco311 said:**
> /usr/include/stdio.h is provided by libc6-dev. try to install the package:
```
sudo apt-get install libc6-dev
```

Ya, it worked..
but why were they not installed automatically even after a full update..
I guess I never had to install them separately in Ubuntu..

---

### Post by Lampi on 2009-08-30
developer packages are only used to **compile** stuff like you just did - they are useless to **operate** the system. thus it makes no sense to install them in the first place, they would only use tons of space and serve nothing. I guess if you install a dev package it's getting updated when a new version comes out and you upgrade.

---

