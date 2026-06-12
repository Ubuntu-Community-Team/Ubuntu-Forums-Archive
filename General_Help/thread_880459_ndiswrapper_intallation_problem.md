---
title: "ndiswrapper intallation problem"
date: 2008-08-05
forum: General Help
---

### Post by akosiartas on 2008-08-05
I am installing the newest version of ndiswrapper but when i compile it, the following codes where generated:

laboratory@administrator:~/Desktop/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/home/laboratory/Desktop/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic M=/home/laboratory/Desktop/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
rm: cannot remove `/home/laboratory/Desktop/ndiswrapper-1.53/driver/.tmp_versions/ndiswrapper.mod': Permission denied
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/laboratory/Desktop/ndiswrapper-1.53/driver'
make: *** [all] Error 2
laboratory@administrator:~/Desktop/ndiswrapper-1.53$ su
Password: 
root@administrator:/home/laboratory/Desktop/ndiswrapper-1.53# make
make -C driver
make[1]: Entering directory `/home/laboratory/Desktop/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic M=/home/laboratory/Desktop/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: Leaving directory `/home/laboratory/Desktop/ndiswrapper-1.53/driver'
make -C utils
make[1]: Entering directory `/home/laboratory/Desktop/ndiswrapper-1.53/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:28: error: expected specifier-qualifier-list before â€˜size_tâ€™
... and etc.

what should i do to resolve these problem? Please help!

---

### Post by cdtech on 2008-08-05
After you did the install, what do you get with "ndiswrapper -l" now?

---

### Post by jimv on 2008-08-05
This may fix the issue:

```
./configure
sudo make clean
sudo make install
```


If that doesn't work, delete the folder, re-extract the files from teh tar.gz archive and run

```
./configure
sudo make install
```

---

