---
title: "Compiling Intel Wireless Drivers"
date: 2005-01-23
forum: Hardware &amp; Laptops
---

### Post by tronda on 2005-01-23
I've downloaded the latest ipw2200 drivers from the [sourceforge site](http://ipw2200.sourceforge.net/). When I try to compile the files, I get the following error message:

```
make -C /lib/modules/2.6.8.1-4-386/build SUBDIRS=/home/xxxx/ipw2200-0.21 MODVERDIR=/home/xxxx/ipw2200-0.21 modules
make: *** /lib/modules/2.6.8.1-4-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
```

Any one knowing why I get this error? Do I lack some kernel source packages?

 :confused:

---

### Post by az on 2005-01-23
"Do I lack some kernel source packages"

Yes.  Install your matching linux-headers package and symlink that directory (/usr/src/linux-headers-2.6.8-1-3-386, for example) to 

/lib/modules/2.6.8.1-4-386/build

---

### Post by RU63 on 2005-01-23
how do u do this?

---

### Post by jerome bettis on 2005-01-23
sudo apt-get install linux-headers-(your version)
sudo ln -s /usr/src/linux-headers-(your version) /lib/modules/2.6.8(version)/build

then

cd to that ipw2200 directory
sudo make
sudo make install
sudo modprobe ipw2200

and that should work

let us know what happens

---

### Post by Spif on 2005-01-23
I wrote a HowTo in this thread: [http://www.ubuntuforums.org/showthread.php?t=12270](http://www.ubuntuforums.org/showthread.php?t=12270)

Hopefully it will solve your problem.

---

