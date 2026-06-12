---
title: "Driver Compiling????"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by rebalde on 2005-07-26
Dist:       Ubuntu 5.04  (the free cd's from Ubuntu)
Modem:  Diamond SupraMax 
Driver:   slmodem-2.9.7  (supplied on the modem install cd.)

After running "make clean" and then running "make", this is what I get:

make
make -c modem all
make[1]: Entring dir './home/rebel/Desktop/modemunzip/slmodem-2.9.7/modem'rebuildprofile...
gcc -wall -g -o -I. -DCONFIG_DEBUG_MODEM -o -modem_main.0 -c modem-main.c
make[1]: gcc: command not found
make[1]: *** [modem-main.o] Error 127
make[1]: leaving directory (repeat the above path)
make: *** [modem] error 2

Obviously I need the gcc-3.3.5 (mentioned in the ModemData.txt) but after a nominal ammount of searching, I've been unable to locate it. I would love a valid link.  Also does the 127 error and the error 2 have any signifgance at this time???

rebel

---

### Post by xethm55 on 2005-07-26
You need to install a package called build-essential. this package is a meta package that contains all of the common development files that are needed to compile.  The error that you recieved is because you do not have gcc (linux c compiler) installed.  the files that are needed are contained on the CD.

either:
```
sudo apt-get update
``` ```
sudo apt-get install build-essential
``` 
or:
use synaptic and search for a package called build-essential

-Xethm55

---

### Post by rebalde on 2005-07-28
My thanks to xethm55
I followed your instructions and I am making progress, however I'm not out of the 
woods quite yet.

Now when I run "make", after approx 30 lines of info, I get these final 10 lines:

make all KERNEL_VER=2.6.0-test7
make[2]: Entering directory `home/rebel/Desktop/modemunzip/slmodem-2.9.7/
               drivers' 
make modules -C /lib/modules/2.6.10-5-386/build  SUBDIRS=/home/ rebel/Desktop/    
               modemunzip/slmodem-2.9.7/drivers
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make  Entering an unknown directorymake: Leaving an unknown directorymake[2]:
               *** [all]Error 2
make[2]: Leaving directory `home/rebel/Desktop/modemunzip/slmodem-2.9.7/
              drivers'
make[1]: *** [all] Error 2
make[1]: Leaving directory `home/rebel/Desktop/modemunzip/slmodem-2.9.7/
               drivers'
make: *** [drivers] Error 2

and that is the end of the "make" command. 

I checked the sub dir "slmodem-2.9.7" and there is no file "build"   
Does anyone know when this file was suppose to be created????

I don't know where to go from here   ](*,) 
Any and all help is graciously accepted.

rebel

---

### Post by strikeforce on 2005-07-28
You can try this link it might help you.

[http://packages.debian.org/unstable/misc/sl-modem-daemon](http://packages.debian.org/unstable/misc/sl-modem-daemon)

---

