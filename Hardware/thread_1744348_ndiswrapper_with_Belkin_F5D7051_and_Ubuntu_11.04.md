---
title: "ndiswrapper with Belkin F5D7051 and Ubuntu 11.04"
date: 2011-04-30
forum: Hardware
---

### Post by DoeJohn__ on 2011-04-30
I'm having some problems with ndiswrapper that I can't fix or figure out, I've spent three hours trying to search on Google for a resolution and attempts to fix it myself, but for nothing to work.

I plug the device in and install ndiswrapper from the Ubuntu Software Centre, then:

```
ndiswrapper -i /home/<user>/drivers/bndiswdm.inf
``` 
That is the correct location of the driver (inf+sys) but it returns an error. The same thing happens but no error when I try to add it via the GUI for ndiswrapper.

I run:
```

ndiswrapper -l

```

and it shows the driver as listed, but when I do:
```

sudo depmod -a

```
it works, but

```

sudo modprobe ndiswrapper 

```
it returns:

> 
FATAL: module 'ndiswrapper' not found


or something similar, I read somewhere that I might need to compile ndiswrapper myself but I have no idea how, I tried to download the source from sourceforge and executed:
```

lsudb
cd /home/<myuser>/ndiswrapper*
tar -xzf *
make uninstall
make
su root
make install

```

(lsudb was used to get the device ID) but it didn't work and returned

> 
<myuser>@Ubuntu:~$ cd /home/<myuser>
<myuser>@Ubuntu:~$ ls
Desktop    examples.desktop  ndiswrapper-1.56.tar.gz  Templates
Documents  Music             Pictures                 Videos
Downloads  ndiswrapper-1.56  Public
<myuser>@Ubuntu:~$ cd ndis*
<myuser>@Ubuntu:~/ndiswrapper-1.56$ ls
AUTHORS    driver   loadndisdriver.8  ndiswrapper.8     README
ChangeLog  INSTALL  Makefile          ndiswrapper.spec  utils
<myuser>@Ubuntu:~/ndiswrapper-1.56$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
<myuser>@Ubuntu:~/ndiswrapper-1.56$ make
make -C driver
make[1]: Entering directory `/home/<myuser>/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.38-8-generic M=/home/<myuser>/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/<myuser>/ndiswrapper-1.56/driver/loader.o
/home/<myuser>/ndiswrapper-1.56/driver/loader.c:834:2: error: unknown field ‘ioctl’ specified in initializer
/home/<myuser>/ndiswrapper-1.56/driver/loader.c:834:2: warning: initialization from incompatible pointer type
make[3]: *** [/home/<myuser>/ndiswrapper-1.56/driver/loader.o] Error 1
make[2]: *** [_module_/home/<myuser>/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/<myuser>/ndiswrapper-1.56/driver'
make: *** [all] Error 2
<myuser>@Ubuntu:~/ndiswrapper-1.56$ su root
Password:
su: Authentication failure
<myuser>@Ubuntu:~/ndiswrapper-1.56$ sudo make install
[sudo] password for <myuser>:
make -C driver install
make[1]: Entering directory `/home/<myuser>/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.38-8-generic M=/home/<myuser>/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/<myuser>/ndiswrapper-1.56/driver/loader.o
/home/<myuser>/ndiswrapper-1.56/driver/loader.c:834:2: error: unknown field ‘ioctl’ specified in initializer
/home/<myuser>/ndiswrapper-1.56/driver/loader.c:834:2: warning: initialization from incompatible pointer type
make[3]: *** [/home/<myuser>/ndiswrapper-1.56/driver/loader.o] Error 1
make[2]: *** [_module_/home/<myuser>/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/<myuser>/ndiswrapper-1.56/driver'
make: *** [install] Error 2
<myuser>@Ubuntu:~/ndiswrapper-1.56$


Any help please?

---

