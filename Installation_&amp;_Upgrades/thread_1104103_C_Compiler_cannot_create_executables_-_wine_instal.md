---
title: "C Compiler cannot create executables - wine installation"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by lufo4 on 2009-03-23
hello, i am new to linux and am trying to run an older version of wine, which i was told would run city of heroes fine, when trying to configure, at the end it tells me that the c compiler cannot create executables

---

### Post by Bachstelze on 2009-03-23
You need to install the whole compilation toolchain, not only the compiler itself.

```
sudo apt-get install build-essential
```

---

### Post by lufo4 on 2009-03-23
thanks for the reply.
I have done this before and tried it again, and still no dice

---

### Post by Bachstelze on 2009-03-23
Something is wrong, then. Please paste the commands you ran and their whole output.

---

### Post by lufo4 on 2009-03-23
output from apt-get:

titan@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


output from ./configure:

titan@ubuntu:~/Downloads/wine-0.9.51$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by Neo_The_User on 2009-03-23
Try:

```

sudo apt-get dist-upgrade && sudo apt-get install gcc g++ libstdc++5 libstdc++6 dh-make debconf debhelper automake autoconf

```

---

### Post by taurus on 2009-03-23
What's the output of this command from a terminal?

```
gcc -v
```

---

### Post by lufo4 on 2009-03-23
output for gcc -v:

titan@ubuntu:~/Downloads/wine-0.9.51$ gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12)

---

### Post by Bachstelze on 2009-03-23
```
See `config.log' for more details.
```

So we need config.log. It's very large and will most likely look totally cryptic to you, just open it in a text editor and paste it to a [pastebin]("http://pastebin.com/"), then give us the link.

---

### Post by lufo4 on 2009-03-23
[http://pastebin.com/m2a7d545b](http://pastebin.com/m2a7d545b)
heres the link

---

### Post by Bachstelze on 2009-03-23
Okay. You need [font="monospace"]gcc-4.3-multilib[/font].

---

### Post by lufo4 on 2009-03-23
i apologize for the late response, 
Thank you, it works great now

---

