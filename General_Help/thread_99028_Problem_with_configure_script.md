---
title: "Problem with configure script"
date: 2005-12-04
forum: General Help
---

### Post by TFleck on 2005-12-04
Im trying to install an audio driver, but when i run ./configure i get this error message:

```
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

Do you know what I can do to solve this?

---

### Post by Ocxic on 2005-12-04
re-install  gcc and install the "build essential" packages that may fix it

---

### Post by TFleck on 2005-12-04
What are the "build essential" packages?

---

### Post by Sutekh on 2005-12-04
```

sudo apt-get install build-essential

```

Will install the "essential-packages" for you.

---

### Post by TFleck on 2005-12-04
The problem now is while checking for kernel version.

```
checking for kernel version... The file /usr/src/linux/include/linux/version.h d oes not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```

What package contains the full kernel sources?
Or is the kernel sources dir wrong?

---

### Post by Sutekh on 2005-12-04
To download your kernel headers you will need to determine your kernel version; at a command line type
```

uname -r

```
You will get something like 2.6.12-10-386.  You would need to then download the headers using
```

sudo apt-get install linux-headers-2.6.12-10-386

```
Of course if your kernel version is different, just adjust that code.

You could also do this in Synaptic just search for "headers" and select to install the correct version.

---

