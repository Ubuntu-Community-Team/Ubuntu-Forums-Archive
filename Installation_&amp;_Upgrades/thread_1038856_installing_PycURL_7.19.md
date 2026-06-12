---
title: "installing PycURL 7.19"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by ko_aung on 2009-01-14
Hi,

I'm using Ubuntu 8.10. I want to use some application which needs PycURL 7.19 installed.

I installed the Python-Devel from terminal

```
sudo aptitude install python-dev
```

and then tried to install PycURL by

```
sudo easy_install-2.5 pycurl
```

When I try to import PycURL from Python2.5, I'm getting this msg

```
Fatal Python error: pycurl: libcurl link-time version is older than compile-time version
Aborted
```

Can anybody point out what I did wrong and how to solve it.

Regards,

ko_aung

---

### Post by ko_aung on 2009-01-14
Solved ;)

I rm the libcurl files inside /usr/lib/ first.

```

cd /usr/lib
sudo rm libcurl.so.x

```

Then link again
```
sudo ln -s /usr/local/lib/libcurl.so.x /usr/lib/libcurl.so.x
```

I'm a beginner to Ubuntu and Linux. So, I don't know how to say it properly or what I did was correct or not. At least, I'm not having the problem importing from Python.

:D

Cheers !
ko_aung

---

### Post by kientt86 on 2010-06-08
I also have same problem,

I did the similar things (remove everything related to libcurl and create link again). It's working fine now.

But any one can explain me why?

---

