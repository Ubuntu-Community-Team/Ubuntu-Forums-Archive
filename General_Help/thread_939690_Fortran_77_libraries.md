---
title: "Fortran 77 libraries"
date: 2008-10-06
forum: General Help
---

### Post by jdemmler on 2008-10-06
**URGENT**

My Fedora version crashed completely yesterday and I installed Ubuntu instead (which already runs on my laptop).

I have to run a script for my PhD that is based on Fortran 77 and several Fortran libraries, which I can't find now in Ubuntu.

Under Fedora the problem is resolved by installing:

```
yum install compat-libf2c
```

I found something called "f2c" and installed it, but that doesn't seem to be right.

P.S.: I installed both gfortran and g77
P.P.S: I get the following error message:

```
error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory
```

---

### Post by kramulous on 2008-10-06
If you:

> cd /
sudo find . -name "*libgfortran*"

Do you see libgfortran.so.1?

Is the path to the location (if found!) located after LD_LIBRARY_PATH when you type "env"?

---

### Post by jdemmler on 2008-10-06
let's see:
> ./usr/lib/libgfortran.so.2.0.0
./usr/lib/libgfortran.so.2
./usr/lib/gcc/i486-linux-gnu/4.2/libgfortranbegin.a
./usr/lib/gcc/i486-linux-gnu/4.2/libgfortran.so
./usr/lib/gcc/i486-linux-gnu/4.2/libgfortran.a
./usr/share/doc/libgfortran2

I can't find LD_LIBRARY_PATH, only:
> PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by jdemmler on 2008-10-06
I guess I have to link the path somehow to the right location???

---

### Post by kramulous on 2008-10-06
Not exactly sure how to proceed here but i'd start by trying to create a symbolic link (will need to sudo):

> ln -s /usr/lib/libgfortran.so.2 /usr/lib/libgfortran.so.1


To check that this worked, if you 

> cd /usr/lib
ls -la | grep libgfortran

You should now see libgfortran.so.1 -> libgfortran.so.2 (or something of the like)

Any joy?

---

### Post by jdemmler on 2008-10-06
I think that might have worked. Thanks.
It definitely starts to go into the script - the rest is probably a bug in my bash script that calls the fortran script.

---

### Post by jdemmler on 2008-10-07
Nope, I cheered too early. I ran the Fortran script by hand instead of redirecting the input and output by bash and it opens up, but then immediately crashes with a "segmentation fault".

---

### Post by kramulous on 2008-10-07
Ahhh, seg fault.  So clear in its explanation.

You have a memory problem in your code.  Usually your array indexing.  When compiling, turn on the array checking ("-fbounds-check" I think)

---

