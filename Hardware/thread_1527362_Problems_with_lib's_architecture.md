---
title: "Problems with lib's architecture"
date: 2010-07-09
forum: Hardware
---

### Post by folone on 2010-07-09
I'm trying to build a project, using ```
$ make
```, but it fails:

```
host SharedLib: libneo_cgi (out/host/linux-x86/obj/lib/libneo_cgi.so) 
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../libz.so when searching for -lz 
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../libz.a when searching for -lz 
/usr/bin/ld: skipping incompatible /usr/lib/libz.so when searching for -lz 
/usr/bin/ld: skipping incompatible /usr/lib/libz.a when searching for -lz 
/usr/bin/ld: cannot find -lz 
collect2: ld returned 1 exit status 
make: *** [out/host/linux-x86/obj/lib/libneo_cgi.so] Error 1 
```

Now look at this library:

```
$ ls -l /usr/lib/libz.so 
lrwxrwxrwx 1 root root 20 2010-07-07 17:08 /usr/lib/libz.so -> /lib/libz.so.1.2.3.3

$ file /lib/libz.so.1.2.3.3
/lib/libz.so.1.2.3.3: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
```

it's for i386 architecture, and I have:

```
$ arch
i686
```

I installed this library like this:
```
sudo apt-get install libz-dev
```

So.. How do I get through this? And how do I make Ubuntu download right libs in the future?
P.S. Ubuntu 10.04 LTS, running on Lenovo ThinkPad SL500, Core 2 DUO CPU.

---

### Post by folone on 2010-07-09
I'm actually not sure, that this is the problem, but.. I'd appreciate any help.
I also asked this one on [SO]("http://stackoverflow.com/questions/3196634/android-build-failure"), but no answer.

---

### Post by folone on 2010-07-09
Resolved this one:
sudo apt-get install lib64z1-dev

---

