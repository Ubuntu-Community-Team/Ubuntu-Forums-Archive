---
title: "Cant compile kernel on 7.04"
date: 2008-09-06
forum: General Help
---

### Post by roberth_001 on 2008-09-06
Im running on 2.6.22.14 by the way.

Im following [this guide](http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6) so that i can enable the ethernet port on my laptop, which supposedly worked out of the box, but not for me. 

Anyway, i get to the point where it tells me to run > make oldconfig

I change directory to where my kernel is extracted to (\home\me\linuz-2.6.22.14\) and run the command, and i generate a huge list of errors instead of something useful
> rob@rob-laptop:~$ cd /home/rob/linux-2.6.22.14
rob@rob-laptop:~/linux-2.6.22.14$ make oldconfig
HOSTCC scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
from scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:116:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:117:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function â€˜usageâ€™:
scripts/basic/fixdep.c:131: warning: implicit declaration of function â€˜fprintfâ€™
scripts/basic/fixdep.c:131: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
scripts/basic/fixdep.c:131: error: â€˜stderrâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:131: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:131: error: for each function it appears in.)
scripts/basic/fixdep.c:132: warning: implicit declaration of function â€˜exitâ€™
scripts/basic/fixdep.c:132: warning: incompatible implicit declaration of built-in function â€˜exitâ€™
scripts/basic/fixdep.c: In function â€˜print_cmdlineâ€™:
scripts/basic/fixdep.c:140: warning: implicit declaration of function â€˜printfâ€™
scripts/basic/fixdep.c:140: warning: incompatible implicit declaration of built-in function â€˜printfâ€™
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:143: error: â€˜NULLâ€™ undeclared here (not in a function)
scripts/basic/fixdep.c: In function â€˜grow_configâ€™:
scripts/basic/fixdep.c:156: warning: implicit declaration of function â€˜reallocâ€™
scripts/basic/fixdep.c:156: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:158: warning: implicit declaration of function â€˜perrorâ€™
scripts/basic/fixdep.c:158: warning: incompatible implicit declaration of built-in function â€˜exitâ€™
scripts/basic/fixdep.c: In function â€˜is_defined_configâ€™:
scripts/basic/fixdep.c:174: warning: implicit declaration of function â€˜memcmpâ€™
scripts/basic/fixdep.c: In function â€˜define_configâ€™:
scripts/basic/fixdep.c:187: warning: implicit declaration of function â€˜memcpyâ€™
scripts/basic/fixdep.c:187: warning: incompatible implicit declaration of built-in function â€˜memcpyâ€™
scripts/basic/fixdep.c: In function â€˜use_configâ€™:
scripts/basic/fixdep.c:206: error: â€˜PATH_MAXâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:214: warning: incompatible implicit declaration of built-in function â€˜memcpyâ€™
scripts/basic/fixdep.c:220: warning: implicit declaration of function â€˜tolowerâ€™
scripts/basic/fixdep.c:222: warning: incompatible implicit declaration of built-in function â€˜printfâ€™
scripts/basic/fixdep.c:206: warning: unused variable â€˜sâ€™
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:225: error: expected declaration specifiers or â€˜...â€™ before â€˜size_tâ€™
scripts/basic/fixdep.c: In function â€˜parse_config_fileâ€™:
scripts/basic/fixdep.c:227: error: â€˜lenâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:233: warning: implicit declaration of function â€˜ntohlâ€™
scripts/basic/fixdep.c:244: warning: implicit declaration of function â€˜isalnumâ€™
scripts/basic/fixdep.c: In function â€˜strrcmpâ€™:
scripts/basic/fixdep.c:261: warning: implicit declaration of function â€˜strlenâ€™
scripts/basic/fixdep.c:261: warning: incompatible implicit declaration of built-in function â€˜strlenâ€™
scripts/basic/fixdep.c: In function â€˜do_config_fileâ€™:
scripts/basic/fixdep.c:272: error: storage size of â€˜stâ€™ isnâ€™t known
scripts/basic/fixdep.c:276: warning: implicit declaration of function â€˜openâ€™
scripts/basic/fixdep.c:276: error: â€˜O_RDONLYâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
scripts/basic/fixdep.c:278: error: â€˜stderrâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:280: warning: incompatible implicit declaration of built-in function â€˜exitâ€™
scripts/basic/fixdep.c:282: warning: implicit declaration of function â€˜fstatâ€™
scripts/basic/fixdep.c:284: warning: implicit declaration of function â€˜closeâ€™
scripts/basic/fixdep.c:287: warning: implicit declaration of function â€˜mmapâ€™
scripts/basic/fixdep.c:287: error: â€˜PROT_READâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:287: error: â€˜MAP_PRIVATEâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:287: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:294: error: too many arguments to function â€˜parse_config_fileâ€™
scripts/basic/fixdep.c:296: warning: implicit declaration of function â€˜munmapâ€™
scripts/basic/fixdep.c:272: warning: unused variable â€˜stâ€™
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:301: error: expected declaration specifiers or â€˜...â€™ before â€˜size_tâ€™
scripts/basic/fixdep.c: In function â€˜parse_dep_fileâ€™:
scripts/basic/fixdep.c:304: error: â€˜lenâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:306: error: â€˜PATH_MAXâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:308: warning: implicit declaration of function â€˜strchrâ€™
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function â€˜strchrâ€™
scripts/basic/fixdep.c:310: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
scripts/basic/fixdep.c:310: error: â€˜stderrâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:311: warning: incompatible implicit declaration of built-in function â€˜exitâ€™
scripts/basic/fixdep.c:313: warning: incompatible implicit declaration of built-in function â€˜memcpyâ€™
scripts/basic/fixdep.c:314: warning: incompatible implicit declaration of built-in function â€˜printfâ€™
scripts/basic/fixdep.c:306: warning: unused variable â€˜sâ€™
scripts/basic/fixdep.c: In function â€˜print_depsâ€™:
scripts/basic/fixdep.c:343: error: storage size of â€˜stâ€™ isnâ€™t known
scripts/basic/fixdep.c:347: error: â€˜O_RDONLYâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
scripts/basic/fixdep.c:349: error: â€˜stderrâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:351: warning: incompatible implicit declaration of built-in function â€˜exitâ€™
scripts/basic/fixdep.c:355: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
scripts/basic/fixdep.c:359: error: â€˜PROT_READâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:359: error: â€˜MAP_PRIVATEâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:359: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:366: error: too many arguments to function â€˜parse_dep_fileâ€™
scripts/basic/fixdep.c:343: warning: unused variable â€˜stâ€™
scripts/basic/fixdep.c: In function â€˜trapsâ€™:
scripts/basic/fixdep.c:378: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
scripts/basic/fixdep.c:378: error: â€˜stderrâ€™ undeclared (first use in this function)
scripts/basic/fixdep.c:380: warning: incompatible implicit declaration of built-in function â€˜exitâ€™
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
rob@rob-laptop:~/linux-2.6.22.14$ 

Anyone know where ive gone wrong. Thanks in advance

---

### Post by Washer on 2008-09-06
try "make xconfig" or "make menuconfig." I've only ever used menuconfig, but i'm 90% sure it imports the current config file from the kernel you booted into. 

If you're paranoid, you can manually copy it from /boot/config-urkernel to the folder & rename it as ".config".

Oh, btw stop using 7.04 thx

---

### Post by Washer on 2008-09-06
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
[http://linuxhelp.150m.com/installs/compile-kernel.htm](http://linuxhelp.150m.com/installs/compile-kernel.htm)

I used those two guides while compiling other stuff. Maybe you can compare notes see what's different.

---

### Post by roberth_001 on 2008-09-06
> **Washer said:**
> try "make xconfig" or "make menuconfig." I've only ever used menuconfig, but i'm 90% sure it imports the current config file from the kernel you booted into. 

If you're paranoid, you can manually copy it from /boot/config-urkernel to the folder & rename it as ".config".

Oh, btw stop using 7.04 thx

why. 7.04 is fine for me, all i want it for is a replacement for vista, which is slow on my laptop for web browsing


Thanks for the advice though, will try it

---

