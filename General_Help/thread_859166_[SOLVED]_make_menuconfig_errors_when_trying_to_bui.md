---
title: "[SOLVED] make menuconfig errors when trying to build custom kernel"
date: 2008-07-14
forum: General Help
---

### Post by Jordanwb on 2008-07-14
I downloaded the source code to kernel version 2.6.26 and extracted it to /usr/src. But when I run "sudo make menuconfig" I get these errors:

> jordanwb@JORDAN-EE97700D:/usr/src/linux-2.6.26$ sudo make menuconfig
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:116:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:117:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function &#8216;usage&#8217;:
scripts/basic/fixdep.c:131: warning: implicit declaration of function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:131: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:131: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:131: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:131: error: for each function it appears in.)
scripts/basic/fixdep.c:132: warning: implicit declaration of function &#8216;exit&#8217;
scripts/basic/fixdep.c:132: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c: In function &#8216;print_cmdline&#8217;:
scripts/basic/fixdep.c:140: warning: implicit declaration of function &#8216;printf&#8217;
scripts/basic/fixdep.c:140: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:143: error: &#8216;NULL&#8217; undeclared here (not in a function)
scripts/basic/fixdep.c: In function &#8216;grow_config&#8217;:
scripts/basic/fixdep.c:156: warning: implicit declaration of function &#8216;realloc&#8217;
scripts/basic/fixdep.c:156: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:158: warning: implicit declaration of function &#8216;perror&#8217;
scripts/basic/fixdep.c:158: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c: In function &#8216;is_defined_config&#8217;:
scripts/basic/fixdep.c:174: warning: implicit declaration of function &#8216;memcmp&#8217;
scripts/basic/fixdep.c: In function &#8216;define_config&#8217;:
scripts/basic/fixdep.c:187: warning: implicit declaration of function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:187: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c: In function &#8216;use_config&#8217;:
scripts/basic/fixdep.c:206: error: &#8216;PATH_MAX&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:214: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:220: warning: implicit declaration of function &#8216;tolower&#8217;
scripts/basic/fixdep.c:222: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c:206: warning: unused variable &#8216;s&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:225: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
scripts/basic/fixdep.c: In function &#8216;parse_config_file&#8217;:
scripts/basic/fixdep.c:227: error: &#8216;len&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:233: warning: implicit declaration of function &#8216;ntohl&#8217;
scripts/basic/fixdep.c:244: warning: implicit declaration of function &#8216;isalnum&#8217;
scripts/basic/fixdep.c: In function &#8216;strrcmp&#8217;:
scripts/basic/fixdep.c:261: warning: implicit declaration of function &#8216;strlen&#8217;
scripts/basic/fixdep.c:261: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
scripts/basic/fixdep.c: In function &#8216;do_config_file&#8217;:
scripts/basic/fixdep.c:272: error: storage size of &#8216;st&#8217; isn&#8217;t known
scripts/basic/fixdep.c:276: warning: implicit declaration of function &#8216;open&#8217;
scripts/basic/fixdep.c:276: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:278: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:280: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:282: warning: implicit declaration of function &#8216;fstat&#8217;
scripts/basic/fixdep.c:284: warning: implicit declaration of function &#8216;close&#8217;
scripts/basic/fixdep.c:287: warning: implicit declaration of function &#8216;mmap&#8217;
scripts/basic/fixdep.c:287: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:287: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:287: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:294: error: too many arguments to function &#8216;parse_config_file&#8217;
scripts/basic/fixdep.c:296: warning: implicit declaration of function &#8216;munmap&#8217;
scripts/basic/fixdep.c:272: warning: unused variable &#8216;st&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:301: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
scripts/basic/fixdep.c: In function &#8216;parse_dep_file&#8217;:
scripts/basic/fixdep.c:304: error: &#8216;len&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:306: error: &#8216;PATH_MAX&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:308: warning: implicit declaration of function &#8216;strchr&#8217;
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
scripts/basic/fixdep.c:310: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:310: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:311: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:313: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:314: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c:306: warning: unused variable &#8216;s&#8217;
scripts/basic/fixdep.c: In function &#8216;print_deps&#8217;:
scripts/basic/fixdep.c:343: error: storage size of &#8216;st&#8217; isn&#8217;t known
scripts/basic/fixdep.c:347: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:349: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:351: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:355: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:359: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:359: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:359: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:366: error: too many arguments to function &#8216;parse_dep_file&#8217;
scripts/basic/fixdep.c:343: warning: unused variable &#8216;st&#8217;
scripts/basic/fixdep.c: In function &#8216;traps&#8217;:
scripts/basic/fixdep.c:378: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:378: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:380: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
jordanwb@JORDAN-EE97700D:/usr/src/linux-2.6.26$       

Wow there's a lot. I tried version 2.6.25.11 and I still get the same errors.

I'm not the only one with the same problem: [http://www.linux-mips.org/archives/linux-mips/2007-05/msg00175.html](http://www.linux-mips.org/archives/linux-mips/2007-05/msg00175.html)

[Solved] sudo apt-get install build-essential libncurses5-dev

---

