---
title: "pkg-config default directory  is prefix/lib/pkgconfig, what is the prefix?"
date: 2008-10-23
forum: General Help
---

### Post by amitm02 on 2008-10-23
from pkg-config man page:
pkg-config retrieves information about packages from  special  metadata
files. These files are named after the package, with the extension .pc.
By default, pkg-config looks in the directory *prefix*/lib/pkgconfig for
these  files; 

what is that *prefix* stand for?

thanks
amit

---

### Post by geirha on 2008-10-24
When you compile and install software manually, you typically select a prefix. The default prefix is /usr/local/ when you compile manually, but ubuntu packages mostly uses /usr/ as prefix, so /usr/lib/pkgconfig is what you are looking for.

Setting prefix=/usr means that binaries get installed in /usr/bin, libraries in /usr/lib, data in /usr/share etc.

---

### Post by amitm02 on 2008-10-24
> **geirha said:**
> When you compile and install software manually, you typically select a prefix. The default prefix is /usr/local/ when you compile manually, but ubuntu packages mostly uses /usr/ as prefix, so /usr/lib/pkgconfig is what you are looking for.

Setting prefix=/usr means that binaries get installed in /usr/bin, libraries in /usr/lib, data in /usr/share etc.

if i understand you correctly, by "setting the prefix", you refer to the usage of --prefix in "./configure --prefix=SOME_DIR".

So, how does "pkg-config --libs --cflags <some-lib>"  knows what prefix i've used for <some-lib> when i manually installed it.

thanks
again
amit

---

### Post by geirha on 2008-10-24
First place it will look is /usr/lib/pkgconfig, but it should also try other commonly used locations, including /usr/local/lib/pkgconfig. 

The strace command will show you all syscalls an application does, in this case you can use that to see what files and directories it attempts to open.
```
strace pkg-config 2>&1 | grep ^open
```

Is pkg-config unable to find a package you've manually compiled?

---

### Post by amitm02 on 2008-10-24
no, i'm just curious. :)

So, the *prefix* in the man page i've stated above, is actually just constant predefined list of directories such as /usr/lib/pkgconfig, /usr/local/lib/pkgconfig etc'?

i would expect a more precise definition in the man page..

---

