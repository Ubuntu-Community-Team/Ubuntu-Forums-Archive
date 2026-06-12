---
title: "Problems installing Elo touch drivers on Ubuntu 10.10"
date: 2010-11-07
forum: Hardware
---

### Post by EzMe on 2010-11-07
Hello all :)

I try installing a Elo touch screen on Ubuntu 10.10. For some reason the drivers wont compile. This is the error msg is get:

```

twan@Studio:/etc/opt/elo/elok_s-source$ sudo make
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/etc/opt/elo/elok_s-source modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /etc/opt/elo/elok_s-source/main.o
In file included from /etc/opt/elo/elok_s-source/main.c:10:
/etc/opt/elo/elok_s-source/elocontrol.h:3: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/etc/opt/elo/elok_s-source/main.o] Error 1
make[1]: *** [_module_/etc/opt/elo/elok_s-source] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [default] Error 2
twan@Studio:/etc/opt/elo/elok_s-source$ 

```

It seems automake cannot find the files and i dont know why. Anyone experiencing the same problems or is there anyone that can help?

Thanks in Advance.

Grtz EzMe

---

### Post by MikeOshea on 2010-11-10
I have the same exact problem and the same exact message. Any help would be appreciated.

I also installed libmotif  
    installation packages 

and CHMOD the directories. Still nothing

---

### Post by steveoriol on 2010-11-23
I have the same exact problem and the same exact message.

---

### Post by Lagerfett on 2011-01-09
I had same problem but found work around. Seems to be a general Makefile problem with kernels near and above version 2.6.34. Directory where autoconf.h resides has changed from
[INDENT][I]/lib/modules/`uname -r`/build/include/linux
[/I][/INDENT]to
[INDENT][I]/lib/modules/`uname -r`/build/include/generated
[/I][/INDENT]
Just create symbolic link of include/generated/autoconf.h in include/linux:

[FONT=Courier New]ln -s /lib/modules/`uname -r`/build/include/generated/autoconf.h /lib/modules/`uname -r`/build/include/linux/autoconf.h

[/FONT]

---

### Post by LinuxDre on 2011-01-12
Hello,

I am following the instructions on
[http://www.elotouch.com/files/install/Elo_Linux_Serial_v3.3.0_i686_Installation_Instructions.txt](http://www.elotouch.com/files/install/Elo_Linux_Serial_v3.3.0_i686_Installation_Instructions.txt)

and I am stuck on 

Step II: --------  Modify the X windows configuration file

I do not have an xorg.conf file.  I am trying to create one as it states in the instructions but I am not sure how to boot into single user mode.

"To generate a copy of xorg.conf based on the current hardware configuration, boot into single user mode and run"
I am new to linux and using Xubuntu 10.10.  Any help would be greatly appreciated.

---

### Post by ihatebillg on 2011-02-26
I am also stuck @
"To generate a copy of xorg.conf based on the current hardware configuration, boot into single user mode and run"

I am using 10.4

---

