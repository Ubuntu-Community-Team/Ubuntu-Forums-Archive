---
title: "gspca help please"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by Anonymity on 2009-09-18
Im kind of new to linux and im trying to get my webcam to work. I have already installed 
[B][I]sudo aptitude install gspca-source camorama and its in usr/src

[/I][/B]
this is where I need help. The website I found says to unpack and change directory to usr/src/modules/gspca then execute "make" but I unpacked it into home/modules/webcam/gspca
[LEFT]so how do I type it into the terminal to do the next part? iv tried all the commands I can think off and it keeps saying no such file or directory.  

Using Jaunty Jackelope 
****[/LEFT]

---

### Post by Partyboi2 on 2009-09-18
Use the change directory command to change to where you have the source eg
```
cd /home/$USER/modules/webcam/gspca
```
then run
```
make
```
Can you provide a link to the instructions you are following?

---

### Post by Anonymity on 2009-09-18
yeah the link is

[http://www.debianadmin.com/how-to-configure-webcam-in-debian-linux.html](http://www.debianadmin.com/how-to-configure-webcam-in-debian-linux.html)

---

### Post by Anonymity on 2009-09-18
ok I got past that part and now when I try to run make I get

scott@desktop:~$ cd /home/$USER/webcam/modules/gspca
scott@desktop:~/webcam/modules/gspca$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/scott/webcam/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/scott/webcam/modules/gspca/gspca_core.o
/home/scott/webcam/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/scott/webcam/modules/gspca/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/scott/webcam/modules/gspca/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/scott/webcam/modules/gspca/gspca_core.c: At top level:
/home/scott/webcam/modules/gspca/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/scott/webcam/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/scott/webcam/modules/gspca/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/scott/webcam/modules/gspca/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/scott/webcam/modules/gspca/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/scott/webcam/modules/gspca/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/scott/webcam/modules/gspca/gspca_core.c: In function ‘spca5xx_probe’:
/home/scott/webcam/modules/gspca/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/scott/webcam/modules/gspca/gspca_core.o] Error 1
make[1]: *** [_module_/home/scott/webcam/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2
scott@desktop:~/webcam/modules/gspca$ 

I have no idea what im doing wrong

---

### Post by Cheezespread on 2009-09-18
Installing the source 
```
sudo aptitude install gspca-source
```

Changing to /usr/src directory
```
cd /usr/src
```

Upacking or Extracintg the package ( I am not sure of the package name . You can check the same in the directory -/usr/src )
```
sudo tar -jxvf gspca.tar.bz2
```

Change from currecnt directory to /usr/src/modules/gspca
```
cd /usr/src/modules/gspca/
```

The steps below for compiling it from the source.
```
make
```
```
sudo make install
```

Rest I am unsure !.Although its updated in the blog post there.

---

### Post by eaglet3d on 2009-09-27
Thank you for the directions, but I get the following errors:

ralph@aspire-5610:/usr/src/modules/gspca$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/usr/src/modules/gspca/gspca_core.c: At top level:
/usr/src/modules/gspca/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_probe’:
/usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2
ralph@aspire-5610:/usr/src/modules/gspca$

There is no semaphore.h anywhere within /usr/src/linux-headers-2.6.28-15-generic or its subdirectories.

---

