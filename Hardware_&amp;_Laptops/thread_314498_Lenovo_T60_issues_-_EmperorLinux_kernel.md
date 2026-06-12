---
title: "Lenovo T60 issues - EmperorLinux kernel"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by cutecuervo on 2006-12-07
I recently installed Edgy on my T60 and haven't been able to get it to 100%.

After a week of reading posts and trying to get everything working I've decided to try and compile an Emperorlinux kernel which is tweaked for laptops.

[http://www.emperorlinux.com/quality/value/kernel/]("http://www.emperorlinux.com/quality/value/kernel/")

**[SIZE="4"]Has anybody compiled the metioned kernel????[/SIZE]**

I am a complete newbie so everything in linux is new for me. This is why I post so I can see if there are benefits from this kernel, before I venture into kernel compilation. Please reply if anybody has used this kernel and if its possible to use it with Ubuntu. I DO NOT want to go back to windows but a new laptop not working correctly makes no sense.

T60 status
Suspend/Hibernate - partially, got it working but after resuming sound dies (principal reason to postpone linux for another 6 months)
Acpi - partially, installed packages and now battery doesn't charge past 70%
Irda - NOT working, haven't tried to fix it.
Fingerprint reader - NOT working

Wireless - Working
ATI card - Working
Thinkpad buttons - Working
Modem - Working
HDAPS - Working

---

### Post by cutecuervo on 2006-12-07
This is to where I got compiling this kernel.


root@NIN:/usr/src/linux# make xconfig
HOSTCC scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
from scripts/basic/fixdep.c:113:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:115:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function &#8216;usage&#8217;:
scripts/basic/fixdep.c:129: warning: implicit declaration of function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:129: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:129: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:129: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:129: error: for each function it appears in.)
scripts/basic/fixdep.c:130: warning: implicit declaration of function &#8216;exit&#8217;
scripts/basic/fixdep.c:130: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c: In function &#8216;print_cmdline&#8217;:
scripts/basic/fixdep.c:138: warning: implicit declaration of function &#8216;printf&#8217;
scripts/basic/fixdep.c:138: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:141: error: &#8216;NULL&#8217; undeclared here (not in a function)
scripts/basic/fixdep.c: In function &#8216;grow_config&#8217;:
scripts/basic/fixdep.c:154: warning: implicit declaration of function &#8216;realloc&#8217;
scripts/basic/fixdep.c:154: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:156: warning: implicit declaration of function &#8216;perror&#8217;
scripts/basic/fixdep.c:156: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c: In function &#8216;is_defined_config&#8217;:
scripts/basic/fixdep.c:172: warning: implicit declaration of function &#8216;memcmp&#8217;
scripts/basic/fixdep.c: In function &#8216;define_config&#8217;:
scripts/basic/fixdep.c:185: warning: implicit declaration of function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:185: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c: In function &#8216;use_config&#8217;:
scripts/basic/fixdep.c:204: error: &#8216;PATH_MAX&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:212: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:218: warning: implicit declaration of function &#8216;tolower&#8217;
scripts/basic/fixdep.c:220: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c:204: warning: unused variable &#8216;s&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:223: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
scripts/basic/fixdep.c: In function &#8216;parse_config_file&#8217;:
scripts/basic/fixdep.c:225: error: &#8216;len&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:231: warning: implicit declaration of function &#8216;ntohl&#8217;
scripts/basic/fixdep.c:242: warning: implicit declaration of function &#8216;isalnum&#8217;
scripts/basic/fixdep.c: In function &#8216;strrcmp&#8217;:
scripts/basic/fixdep.c:255: warning: implicit declaration of function &#8216;strlen&#8217;
scripts/basic/fixdep.c:255: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
scripts/basic/fixdep.c: In function &#8216;do_config_file&#8217;:
scripts/basic/fixdep.c:266: error: storage size of &#8216;st&#8217; isn&#8217;t known
scripts/basic/fixdep.c:270: warning: implicit declaration of function &#8216;open&#8217;
scripts/basic/fixdep.c:270: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:272: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:272: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:274: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:276: warning: implicit declaration of function &#8216;fstat&#8217;
scripts/basic/fixdep.c:278: warning: implicit declaration of function &#8216;close&#8217;
scripts/basic/fixdep.c:281: warning: implicit declaration of function &#8216;mmap&#8217;
scripts/basic/fixdep.c:281: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:281: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:281: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:288: error: too many arguments to function &#8216;parse_config_file&#8217;
scripts/basic/fixdep.c:290: warning: implicit declaration of function &#8216;munmap&#8217;
scripts/basic/fixdep.c:266: warning: unused variable &#8216;st&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:295: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
scripts/basic/fixdep.c: In function &#8216;parse_dep_file&#8217;:
scripts/basic/fixdep.c:298: error: &#8216;len&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:300: error: &#8216;PATH_MAX&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:302: warning: implicit declaration of function &#8216;strchr&#8217;
scripts/basic/fixdep.c:302: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
scripts/basic/fixdep.c:304: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:304: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:305: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:307: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c:300: warning: unused variable &#8216;s&#8217;
scripts/basic/fixdep.c: In function &#8216;print_deps&#8217;:
scripts/basic/fixdep.c:337: error: storage size of &#8216;st&#8217; isn&#8217;t known
scripts/basic/fixdep.c:341: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:343: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:343: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:345: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:353: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:353: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:353: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:360: error: too many arguments to function &#8216;parse_dep_file&#8217;
scripts/basic/fixdep.c:337: warning: unused variable &#8216;st&#8217;
scripts/basic/fixdep.c: In function &#8216;traps&#8217;:
scripts/basic/fixdep.c:372: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:372: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:374: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
root@NIN:/usr/src/linux#

I used the following Howto and everything went fine until make xconfig

[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

Any ideas, suggestions?

---

