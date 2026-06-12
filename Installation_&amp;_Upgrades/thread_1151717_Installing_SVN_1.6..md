---
title: "Installing SVN 1.6.*?"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by alzorz on 2009-05-07
I need to install SVN 1.6.* on my Ubuntu Intrepid Ibex installation. Feels like I've tried everything :S. First I downloaded the source file from tigris and when configuring it didn't find APR. So I downloaded APR and configuring works but when I get to make I get this.
```
anton@anton-laptop:~/apr-1.2.11$ make
make[1]: Entering directory `/home/anton/apr-1.2.11'
make[1]: Nothing to be done for `local-all'.
make[1]: Leaving directory `/home/anton/apr-1.2.11'
```
Also I tried installing the deb packace from debian and then I got "Error: Dependency is not satisfiable: libsvn1" so I downloaded and reinstalled libsvn1 and tried again but still the same message, meaning I can't install :S. 

Really need to get this to work, working in a school project and they are using TortoiseSVN which is version 1.6.* so I can't do anything because I got to old version =(.

All help is appreciated.

Alzorz

---

### Post by hansdown on 2009-05-07
Hi alzorz.

This link might help.

[http://blog.lv25.com/2009/04/build-subversion-16-on-ubuntu-810.html](http://blog.lv25.com/2009/04/build-subversion-16-on-ubuntu-810.html)

---

### Post by alzorz on 2009-05-08
Thanks, that worked great =)

---

### Post by hansdown on 2009-05-08
Glad you got it going.

---

