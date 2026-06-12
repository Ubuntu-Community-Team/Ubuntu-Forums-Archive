---
title: "error while loading shared libraries: libstdc++-libc6.2-2.so.3"
date: 2008-09-22
forum: General Help
---

### Post by Magoffire on 2008-09-22
For the past while, I have been suffering with an annoying error whenever I try to run a certain application.  What gets me is it was working fine, then when I went to use it later, it failed.  There was a week or so between, so I suppose any number of things could have gone wrong.

The application I am using is called JAD, it is a Java decompiler.

The error is as follows:
```
./jad: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```

Upon research, I was able to find out that it is indeed a C++ library, but I was unable to find any solutions to my problem.

I am working on a time critical project and I need a solution as fast as possible, so thank you VERY much to anyone who can help.

---

### Post by Magoffire on 2008-09-22
I guess no one knows?

---

### Post by Magoffire on 2008-09-22
Darn.

---

### Post by shemapi on 2008-09-24
hi,
I think, this library is not available over the ubuntu.
You have to find the package where it is contained and install it.
So, i'm working over ubuntu hardy heron and I look for it on
[http://www.debian.org/distrib/packages#search_contents](http://www.debian.org/distrib/packages#search_contents)
there you see what packages contain the library you need. Depending of your pc architecture you must choose one, in my case i choose libstdc++2.10-glibc2.2 and then you have to download the exact one you need for your specific architecture from the server you'd prefer.
After that you only need to install that package(dpkg).
I hope this help you.

---

### Post by Eder Santos on 2009-09-01
Thanks that solve my problem.

[http://packages.debian.org/etch/libstdc++2.10-glibc2.2](http://packages.debian.org/etch/libstdc++2.10-glibc2.2)

---

### Post by 1jackjack on 2009-12-17
+1 for [http://packages.debian.org/etch/libstdc++2.10-glibc2.2](http://packages.debian.org/etch/libstdc++2.10-glibc2.2)

thanks

---

### Post by dstath on 2010-05-24
had the same problem. Solved by adding libstdc++5 from Synaptic

---

### Post by Dilyan on 2012-07-07
In case anybody has this problem in Ubuntu 12.04, none of the above methods work. The solution is to use the statically-linked JAD executable, found currently at the official mirror site:
[http://www.varaneckas.com/jad/](http://www.varaneckas.com/jad/)
[http://www.varaneckas.com/jad/jad158e.linux.static.zip](http://www.varaneckas.com/jad/jad158e.linux.static.zip)

---

### Post by oldos2er on 2012-07-07
Closed; please don't bump old threads.

---

