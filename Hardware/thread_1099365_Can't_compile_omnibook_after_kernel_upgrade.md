---
title: "Can't compile omnibook after kernel upgrade"
date: 2009-03-18
forum: Hardware
---

### Post by wwnliu on 2009-03-18
Dear all,

I've been using the omnibook module with my Toshiba notebook and ubuntu 8.10 without any problem. But after a recent kernel upgrade to version 2.6.27-11, I can no longer compile the omnibook source code. Whenever I tried to make install the file in terminal, it returns the following error message.

```
william@william-laptop:~/Other_software/omnibook-2.20070211$ sudo make install
[sudo] password for william: 
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/william/Other_software/omnibook-2.20070211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/william/Other_software/omnibook-2.20070211/ac.o
/home/william/Other_software/omnibook-2.20070211/ac.c:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ac_driver’
/home/william/Other_software/omnibook-2.20070211/ac.c: In function ‘__check_ac’:
/home/william/Other_software/omnibook-2.20070211/ac.c:57: error: ‘ac_driver’ undeclared (first use in this function)
/home/william/Other_software/omnibook-2.20070211/ac.c:57: error: (Each undeclared identifier is reported only once
/home/william/Other_software/omnibook-2.20070211/ac.c:57: error: for each function it appears in.)
/home/william/Other_software/omnibook-2.20070211/ac.c: At top level:
/home/william/Other_software/omnibook-2.20070211/ac.c:57: error: ‘ac_driver’ undeclared here (not in a function)
make[2]: *** [/home/william/Other_software/omnibook-2.20070211/ac.o] Error 1
make[1]: *** [_module_/home/william/Other_software/omnibook-2.20070211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [omnibook.ko] Error 2
```

Hope someone will have the solution for this problem.

---

### Post by wolo on 2009-03-18
I solved the problem like this.

downloaded rpm source package from opensuse:
wget ftp5.gwdg.de/pub/opensuse/update/11.1/rpm/src/omnibook-20080627-1.1.6.src.rpm

unpacked:
rpm2cpio omnibook-20080627-1.1.6.src.rpm | cpio -i omnibook-2.20080627.tar.bz2

and proceeded as usual. Compiling worked without any problems.

Cheers

---

### Post by wwnliu on 2009-03-19
Thanks, that new package does work.

---

### Post by Nareto on 2009-05-28
There's one thing I don't understand: why on the official sourceforge page
[http://sourceforge.net/project/showfiles.php?group_id=48623&package_id=47019]("http://sourceforge.net/project/showfiles.php?group_id=48623&package_id=47019")
the latest version is from 2006 while the link from above is from 06/27/2008?

---

### Post by apexofservice on 2010-09-14
agree, I was attempting and failing with 2006 and 2007 versions until I saw this thread.  

my only problem now: I've never used rpms before.  I followed the syntax in the post above to 

wget source
rpm2cpio 

I'm not sure what to do next.  It looked like the rpm2cpio command did some compiling.  Now I'm running

find / -name "omnibook-2008*" 

to try to find out what might have happened.  

$modprobe omnibook 

still says not found, so I guess I'm not that far along yet.

---

