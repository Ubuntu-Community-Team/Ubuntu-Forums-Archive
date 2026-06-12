---
title: "libxml2 library"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by v.manyu on 2009-07-27
i am trying to install Kannel.org wap n sms gateway on my UBUNTU
but when i ./configure the package, at the end it gives "unable to find libxml2-config"
libxml2 package is installed in synaptics package manager
pls tell me wat the problem may be

thank u,

Abhimanyu

---

### Post by Claus7 on 2009-07-27
Hello,

this for one reason or the other can happen, even though you have installed the package. 3 things to check:

i)Does the version of the library the program you want to install is the appropriate one? I mean that the libxml2 library is the right version? In my system I can see a lot. So installing some of them might not be a bad idea.

ii)Have you installed the dev package of that library (beside the name in synaptic is sais explicitly dev)

iii)Can you provide during configuration the path where the missing file exists? (e.g. ./configure --with-libxml-dir=/usr/bin)

Normaly if it is in your path, it should be recognised. One other thing that I can tell you, which I did in the end in a similar situation, was to download the missing library and install it myself. Then compile the program you want, giving the path to your newly compiled library.

Regards!

---

