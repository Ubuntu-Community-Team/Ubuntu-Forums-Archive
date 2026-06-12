---
title: "NEED a favour from all of the UBUNTU USERS"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by gprateek on 2009-08-07
Hello all, i am at the initial stages of working with UBUNTU 9.04 cd edition.

1.
I wanted to install some of the application and even tried with WINE  , but they didnt work.

However , I got a substitute of one of the applications "ipmsg" and wanted to install it . So I downloaded the package built for Linux . its link is [http://www.ipmsg.org/archive/g2ipmsg-0.9.6.tar.gz](http://www.ipmsg.org/archive/g2ipmsg-0.9.6.tar.gz) 

BUT ............  when I try to install it , it shows some errors and the setup does not complete ...... 
             $./configure.sh      : the process, after some time gives the msg that GNU tools are not available ,  i cant even find a GNU install in Add/Remove Applications 

 :(

2.
:confused:
I have to code programs for C++ but dont know hoe to do it in UBUNTU . Earlier I have made them only in TC .  Pls help me , this one is urgrnt as a student .

---

### Post by phillw on 2009-08-07
[SIZE=2]gcc is the default C Compiler ... (Gnu C Compiler)

g++ is for C++

try man gcc   or man g++ from a terminal window[/SIZE]. 

[SIZE=2]This link will be of more help to you...

[http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html](http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html)

Regards,

Phill.
[/SIZE]

---

### Post by Cheesemill on 2009-08-07
To install all of the necesary tools to compile programs from source you need to do:
```
 
sudo apt-get install build-essential

```For certain programs that need to compile kernel modules you may need to do:
```
 
sudo apt-get install linux-headers-`uname -r`

```as well.

---

### Post by slakkie on 2009-08-07
Maybe install xipmsg, available in the repos of 8.04.. 

If you do ./configure -n you can see what it will do, but it will not do it, handy for checking deps...

---

### Post by gprateek on 2009-08-07
Hi everyone, 

I got the soln for the 2nd prob of C++ : using the DOSBOX app (as was done when I used VISTA to run in full screen)

However .. the 1st problem is IRRITATING ME as I cannot use my University LAN to transfer files and folder perfectly. 

:(
This time the  $./configure  was working fine , and when I run  $ make install  =>IT SHOWS SOME ERRORS WHICH SAID THAT IT DOES NOT HAS PRIVILEGES TO FORM ITS OWN DIRECTORY IN /usr/local     ..... 

PLS ...... PLS HELP ME..............



PROBLEM VIEW:
./configure  ---works fine
make          ---works fine

make install      -----the following output is obtained

"
prateek@prateek-laptop:~/DOWNLOADS/g2ipmsg-0.9.6$ make install
Making install in src
make[1]: Entering directory `/home/prateek/DOWNLOADS/g2ipmsg-0.9.6/src'
make[2]: Entering directory `/home/prateek/DOWNLOADS/g2ipmsg-0.9.6/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'g2ipmsg' '/usr/local/bin/g2ipmsg'
/usr/bin/install: cannot create regular file `/usr/local/bin/g2ipmsg': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/prateek/DOWNLOADS/g2ipmsg-0.9.6/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/prateek/DOWNLOADS/g2ipmsg-0.9.6/src'
make: *** [install-recursive] Error 1
prateek@prateek-laptop:~/DOWNLOADS/g2ipmsg-0.9.6$

"

---

### Post by dagrump on 2009-08-07
That would be sudo make install, you need root permissions.

---

### Post by gprateek on 2009-08-07
> **dagrump said:**
> That would be sudo make install, you need root permissions.
U made it look too simple......... thanks dude......

---

### Post by dagrump on 2009-08-07
Some times the simple fix is right in front of us, but we overlook it.

---

