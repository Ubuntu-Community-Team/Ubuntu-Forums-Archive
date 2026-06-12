---
title: "Libboost 1.38 on Hardy ?"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by Morfi777 on 2009-06-01
Hello,

I have ubuntu 8.04 LTS and I need to install Liboost 1.38 package which is only on Karmic

How can I do it on my OS ? I can't change it.


I downloaded the source, unpacked, run ./configure, sudo make and I got followin error:
```
admin@aaaaa:/home/bot/boost_1_38_0$ sudo make
./tools/jam/src//bjam -sICU_PATH=/usr --user-config=user-config.jam
/bin/sh: ./tools/jam/src//bjam: No such file or directory
Not all Boost libraries built properly.
```

I went to /tools/jam/src/, run ```
sh build.sh
```but still I get same error.


Any help will be appreciated.
Thanks!

---

### Post by Morfi777 on 2009-06-01
please..

---

### Post by Morfi777 on 2009-06-01
or maybe other than 1.38 ?

---

