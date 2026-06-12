---
title: "Scanjet 5100C [bangs head on table]"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by Tvanover on 2008-02-25
The infamous HP ScanJet 5100C

I am trying to follow the steps in [http://ubuntuforums.org/showthread.php?t=441180]("http://ubuntuforums.org/showthread.php?t=441180")with no luck.  I hit step 5 and cannot make.  Even with the modifications.

```

molly@molly-butu:~/Downloads/Source/ppscsi-beta2$ make
make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/molly/Downloads/Source/ppscsi-beta2/ppscsi.o
In file included from /home/molly/Downloads/Source/ppscsi-beta2/ppscsi.c:55:
/home/molly/Downloads/Source/ppscsi-beta2/ppscsi.h:16:30: error: linux/autoconfig.h: No such file or directory
make[2]: *** [/home/molly/Downloads/Source/ppscsi-beta2/ppscsi.o] Error 1
make[1]: *** [_module_/home/molly/Downloads/Source/ppscsi-beta2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

```

I have tried installing:
sane-backends-1.0.19.tar.gz
sane-1.0.13.hp.1.06.tar.gz

They install but I still cannot see the printer.  I am using Ubuntu feisty 7.04

---

### Post by apjone on 2008-02-25
> **Tvanover said:**
> The infamous HP ScanJet 5100C

I am trying to follow the steps in [http://ubuntuforums.org/showthread.php?t=441180]("http://ubuntuforums.org/showthread.php?t=441180")with no luck.  I hit step 5 and cannot make.  Even with the modifications.

```

molly@molly-butu:~/Downloads/Source/ppscsi-beta2$ make
make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/molly/Downloads/Source/ppscsi-beta2/ppscsi.o
In file included from /home/molly/Downloads/Source/ppscsi-beta2/ppscsi.c:55:
/home/molly/Downloads/Source/ppscsi-beta2/ppscsi.h:16:30: error: linux/autoconfig.h: No such file or directory
make[2]: *** [/home/molly/Downloads/Source/ppscsi-beta2/ppscsi.o] Error 1
make[1]: *** [_module_/home/molly/Downloads/Source/ppscsi-beta2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

```

I have tried installing:
sane-backends-1.0.19.tar.gz
sane-1.0.13.hp.1.06.tar.gz

They install but I still cannot see the printer.  I am using Ubuntu feisty 7.04


Which version of ubuntu are you running?

Take a look at 
[http://www.sane-project.org/man/sane-hp.5.html](http://www.sane-project.org/man/sane-hp.5.html)
this is the sane official website.

---

### Post by Tvanover on 2008-02-25
Gah, I fell for the classic blunder.  I changed the config.h line to autoconfig.h not autoconf.h.

---

### Post by apjone on 2008-02-25
> **Tvanover said:**
> Gah, I fell for the classic blunder.  I changed the config.h line to autoconfig.h not autoconf.h.

All working then ??

---

### Post by haydnc on 2008-05-15
Just for the record, this currently does not work on Hardy Heron (8.04). My original instructions leave you with what can only be described as a scanner shaped paper weight - or, in other words exactly what you had before trying to get your HP Scanjet 5100C up and running.

The problem is there have been some significant alterations in some of the modules that ppscsi needs to compile and they invalidate my instructions in the previously mentioned thread.

I'm still looking for a solution that doesn't involve buying a new scanner for Hardy.

---

### Post by haydnc on 2008-05-18
I've posted some instructions [here]("http://ubuntuforums.org/showthread.php?t=782242") for how to at least get ppscsi to compile on Hardy.

Unfortunately no-one has posted any feedback about whether their scanner works after building and installing the files - and it doesn't work for me but I've been unable to work out why.

If anyone tries it and it works please let me know.

---

