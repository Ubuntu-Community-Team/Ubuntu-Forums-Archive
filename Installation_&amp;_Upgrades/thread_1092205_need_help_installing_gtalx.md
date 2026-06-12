---
title: "need help installing gtalx"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by NO2 on 2009-03-10
i was trying to install gtalx
when i run ./make i get this:

mv -f .deps/stream.Tpo .deps/stream.Plo
/bin/bash ../../libtool --silent --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I../.. `pkg-config --cflags gtk+-2.0`    -DPOSIX -g -O2 -MT ssladapter.lo -MD -MP -MF .deps/ssladapter.Tpo -c -o ssladapter.lo ssladapter.cc
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

what should i do?

---

### Post by Partyboi2 on 2009-03-10
Looks like you need to install the libgtk2.0-dev package
```
sudo apt-get install libgtk2.0-dev
```

---

### Post by NO2 on 2009-03-10
thank you

---

### Post by jukzh on 2009-06-11
Hello!
I need help
Runnig make script error, I can't find out what's problem
```

/usr/bin/ld: cannot find -lavcodec

```
What is that lavcodec?
Regards,
JK

---

### Post by Partyboi2 on 2009-06-11
> **jukzh said:**
> Hello!
I need help
Runnig make script error, I can't find out what's problem
```

/usr/bin/ld: cannot find -lavcodec

```What is that lavcodec?
Regards,
JK
Hi, try installing the libavcodec-dev package
```
 sudo apt-get install libavcodec-dev 
```

---

