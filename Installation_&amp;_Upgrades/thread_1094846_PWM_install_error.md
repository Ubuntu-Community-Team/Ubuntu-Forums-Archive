---
title: "PWM install error"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by grin82 on 2009-03-13
hello im running Ubuntu version > ubuntu-8.10-desktop

anyway im trying to install a window manager called PWM, ive downloaded the file and unpacked it.
But when i try to give it the make command i get the follow error message **>**

snprint_2.2/snprintf.c: In funtion 'vasprintf':
snprint_2.2/snprintf.c:455: error: incompatible types in assignment
snprint_2.2/snprintf.c: In funtion 'vasprintf':
snprint_2.2/snprintf.c:568: warning: signed and unsigned type in condtional expression
snprint_2.2/snprintf.c:717: warning: signed and unsigned type in condtional expression
make[1]:*** [snprintf_2.2/snprintf.o] Error 1]
make[1]: Leaving directory `/home/grin/pwm-20070720/libtu'
make: *** [subdir] Error 2

the only thing ive found about it when i googled was from a fellow using a linux version called Gentoo Linux he had an error messege simulair to mine **>** When trying to emerge pwm, the build exits with the following error:

gcc -O2 -mcpu=G4 -mtune=G4 -maltivec -mabi=altivec -fno-strict-aliasing -pipe  
-I./include  -ansi -D_POSIX_SOURCE -c snprintf_2.2/snprintf.c -o
snprintf_2.2/snprintf.o
snprintf_2.2/snprintf.c: In function 'vasprintf':
snprintf_2.2/snprintf.c:455: error: incompatible types in assignment
make[1]: *** [snprintf_2.2/snprintf.o] Error 1
make[1]: Leaving directory
`/var/tmp/portage/pwm-1.0.20030617/work/pwm-20030617/libtu-20030528'

and he solved the problem by doing as follow**>**
"Arguably this is a bug in PWM, however, for those systems that have a built-in asprintf (as does Linux) it is not needed to build the supplied snprintf.c. All that is needed is that HAS_SYSTEM_ASPRINTF is defined. This can be done either in the system.mk file of pwm (or set by the ebuild), or, as a workaround and for those who want to emerge it right now:

HAS_SYSTEM_ASPRINTF=1 emerge pwm

This compiles flawlessly on my system."

im new too linux and have no idee how im suposed to do to try that.
so my question is if someone know how im suposed to do it the way he describes it or have a better way

---

### Post by cariboo on 2009-03-13
It may be an idea to contact the person that came up with the fix.

Jim

---

### Post by grin82 on 2009-03-13
well its a 3-4 years old messege

---

