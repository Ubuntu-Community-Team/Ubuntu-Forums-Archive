---
title: "apt and python problems"
date: 2005-11-17
forum: General Help
---

### Post by dontodd on 2005-11-17
I think I was having a problem with my reiserfs because I had all sorts of weird permissions errors. I ran reiserfsck and fixed the problems (for instance I couldn't ls -lh /usr/bin/python2.4--permission denied). Now I don't even have python 2.4 in /usr/bin, and when I try to install with apt-get I get the message 

Setting up python2.4 (2.4.2-1) ...
Compiling python modules in /usr/lib/python2.4 ...
/var/lib/dpkg/info/python2.4.postinst: line 20: /usr/bin/python2.4: No such file or directory
dpkg: error processing python2.4 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python2.4
E: Sub-process /usr/bin/dpkg returned an error code (1)

This pretty much ruins everything for me :( 

Can anybody suggest a possible solution that doesn't require a fresh install?

Thanks!

---

### Post by kruz on 2005-11-17
let me get this out of the way and say
you do run sudo in front of ur command right?

---

### Post by dontodd on 2005-11-17
Kruz: yes.

---

