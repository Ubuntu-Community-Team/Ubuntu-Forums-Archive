---
title: "[SOLVED] binary package instillation and ROOTSYS"
date: 2008-08-28
forum: General Help
---

### Post by boldexplorer on 2008-08-28
Hello I am trying to install a number of packages, however, the packages keep failing. The packages are all downloaded in binary so they need to be compiled. That is not hard in theory...
The instructions say that I need to set $ROOTSYS.
What is this? How does one set it? To where? WHY? How does this cause problems? 

Please can someone educate me? Thanks!

---

### Post by nbayiha on 2008-08-28
What are you trying to install , can you show us the thread you are following ?

---

### Post by boldexplorer on 2008-08-28
I am trying to install Midas, ROOT and ROODY
so if I try and compile the programme this the output: 
    brett@brett-desktop:~/midas/zlib-1.0.4$ make
     cc -O -o example example.o -L. -lz
     /usr/bin/ld: errno: TLS definition in /lib/libc.so.6 section .tbss
    mismatches non-TLS reference in ./libz.a(gzio.o)
     /lib/libc.so.6: could not read symbols: Bad value
     collect2: ld returned 1 exit status
     make: *** [example] Error 1

    And it is similar for root.

>>start with root build and make sure $ROOTSYS points to the correct place
>>and $PATH and $LD_LIBRARY_PATH are set properly to make root run fine

then follow [http://daq.tlabs.ac.za/software/psi-midas](http://daq.tlabs.ac.za/software/psi-midas)
use svn to get the latest version  for midas and mxml
do the commands in /opt
then go into /opt/midas
check $ROOTSYS is defined
and then type make
then make install
then go into /opt/midas/examples/experiment
in there is a dummy experiment with a couple of start scripts see if you can get that test experiment to work, it uses a dummy camac crate, no hardware required.

---

### Post by boldexplorer on 2008-09-08
Problem solved.:)
the instructions were calling for a path name on where to install the programme. So one setup ROOTSYS to be /home/user/root for example. Then the programme installed into /home/user/root

All happy! 
Have a good day and happy Linuxing!

---

