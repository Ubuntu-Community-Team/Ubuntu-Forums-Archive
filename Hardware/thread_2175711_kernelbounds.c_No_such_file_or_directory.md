---
title: "kernel/bounds.c: No such file or directory"
date: 2013-09-20
forum: Hardware
---

### Post by mamboknave on 2013-09-20
I'm trying to make the card-reader of my laptop working.

I'm with Ubuntu 10.04, 64b. The output of the attempt is:

>> sudo make
...
gcc: kernel/bounds.c: No such file or directory
gcc: no input files
make[2]: *** [kernel/bounds.s] Error 1
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-51-generic'
make: *** [default] Error 2

The kernel source was installed with 'sudo apt-get install linux-source' and is available as:

/usr/src/linux-source-2.6.32/

In it I see the missing file:

/usr/src/linux-source-2.6.32/kernel/bounds.c

At this point I'm clueless about how to fix this and I'm eagerly seeking advice.
Perhaps, the linux-source is not installed properly? I did install it twice by unzipping/untarring the tar file.

Thanks in advance.

---

