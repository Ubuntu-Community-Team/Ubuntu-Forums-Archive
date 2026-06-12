---
title: "making a .deb"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by johnh10000 on 2009-07-23
hi, as i'm using jaunty, and I want to use idjc, i found out recently i have to recompile it. done.

now i have it working.  how would i go about making a debian/ubuntu package, the idea being it will go off ang get it's deps.

cheers gang

---

### Post by lisati on 2009-07-23
[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

---

### Post by Leslie Viljoen on 2009-07-23
I also found this to be an extremely useful article if you want to quickly make a few changes to a package in the repository and then recompile it:

[http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/opensource/0596527209/i-0596527209-chp-6-sect-10.html](http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/opensource/0596527209/i-0596527209-chp-6-sect-10.html)

---

### Post by johnh10000 on 2009-07-23
I found this debianpackagemaker thingy anyone got it to work.

johnh10000@tux:~$ debianpackagemaker
Cannot open assembly '/tmp/DebianPackageMaker/usr/lib/debianpackagemaker/DebianPackageMaker.exe': No such file or directory.
johnh10000@tux:~$ 

i installed it from a .deb so....

---

### Post by lisati on 2009-07-23
> **johnh10000 said:**
> I found this debianpackagemaker thingy anyone got it to work.

johnh10000@tux:~$ debianpackagemaker
Cannot open assembly '/tmp/DebianPackageMaker/usr/lib/debianpackagemaker/DebianPackageMaker.exe': No such file or directory.
johnh10000@tux:~$ 

i installed it from a .deb so....

Looks like it uses something to do with Windows - ".exe" is a MS-DOS and Windows file format

---

### Post by johnh10000 on 2009-07-23
> **lisati said:**
> Looks like it uses something to do with Windows - ".exe" is a MS-DOS and Windows file format

not much to do today, well apart from setting up a mail server on the other box, easy now, half hour tops.  So I'll grab the source, and see where we go from there.

---

### Post by johnh10000 on 2009-07-23
> **johnh10000 said:**
> not much to do today, well apart from setting up a mail server on the other box, easy now, half hour tops.  So I'll grab the source, and see where we go from there.

found a workaround for this problem, from a year ago !!!

[http://code.google.com/p/debianpackagemaker/issues/detail?id=7](http://code.google.com/p/debianpackagemaker/issues/detail?id=7)

---

### Post by johnh10000 on 2009-07-23
> **johnh10000 said:**
> found a workaround for this problem, from a year ago !!!

[http://code.google.com/p/debianpackagemaker/issues/detail?id=7](http://code.google.com/p/debianpackagemaker/issues/detail?id=7)

it wants something called gtk-sharp2
no problem get the source that wants

checking for GAPI... configure: error: Package requirements (gapi-2.0 >= 2.12.2) were not met:

No package 'gapi-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAPI_CFLAGS
and GAPI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

cant find version 2 anywhere :(

you'd ahave thought it would have all this lot with it.

---

### Post by Partyboi2 on 2009-07-23
Hi, try installing the 'gtk-sharp2-gapi' package
```
sudo apt-get install gtk-sharp2-gapi
```

---

### Post by johnh10000 on 2009-07-23
> **Partyboi2 said:**
> Hi, try installing the 'gtk-sharp2-gapi' package
```
sudo apt-get install gtk-sharp2-gapi
```

Cheers thats got a makefile.  will report back after compile etc,
see what else it wants.

after all this it had better work ;)

---

