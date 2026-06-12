---
title: "Cpmpiling Driver (works fine in openSuSE)"
date: 2009-06-28
forum: Hardware
---

### Post by mhdbnoimi on 2009-06-28
Hi all,

I want to define my modem through compiling its driver. In openSuSE it works fine but in ubuntu compiling process didn't complete correctly because there are many missed header files.

So could you please tell me what's wrong?

Notes:
* I'm using:
```
ubuntu 8.10
gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2
```
* In the attached files you'll find build log and driver source code.
* Please be patient I've migrated from openSuSE a week ago.

---

### Post by Ayuthia on 2009-06-28
It looks like you might have forgotten to attach the logs.

By the way, have you already installed build-essential?  If I recall correctly, it will help provide some of the missing header files.

---

### Post by mhdbnoimi on 2009-06-28
sorry, now u can find the attachments

---

### Post by mhdbnoimi on 2009-06-28
Do I need kernel source code for compiling this driver ? I just want a tip.

---

### Post by mhdbnoimi on 2009-07-11
After installing kernel headers I got the following errors:

```
root@mbnoimi:~/Desktop/CNet/Modem/Linux/release# make all
cd src/hamcore; make hamcore-release
make[1]: Entering directory `/home/mbnoimi/Desktop/CNet/Modem/Linux/release/src/hamcore'
cc -Wall -O -I /usr/include -I../inc   -c -o coredrv.o coredrv.c
In file included from hamcore.h:38,
                 from coredrv.c:33:
hamdefs.h:45:25: error: linux/config.h: No such file or directory
hamdefs.h:89:8: warning: extra tokens at end of #endif directive
In file included from coredrv.c:33:
hamcore.h:39:27: error: linux/proc_fs.h: No such file or directory
In file included from coredrv.c:33:
hamcore.h:233: warning: &#8216;struct file&#8217; declared inside parameter list
hamcore.h:233: warning: its scope is only this definition or declaration, which is probably not what you want
hamcore.h:261:8: warning: extra tokens at end of #endif directive
coredrv.c:35:26: error: linux/module.h: No such file or directory
coredrv.c:36:25: error: linux/delay.h: No such file or directory
coredrv.c: In function &#8216;hamcore_init&#8217;:
coredrv.c:54: error: &#8216;printk&#8217; undeclared (first use in this function)
coredrv.c:54: error: (Each undeclared identifier is reported only once
coredrv.c:54: error: for each function it appears in.)
coredrv.c:55: error: &#8216;schedule&#8217; undeclared (first use in this function)
coredrv.c:56: warning: implicit declaration of function &#8216;printk&#8217;
coredrv.c:56: error: &#8216;KERN_DEBUG&#8217; undeclared (first use in this function)
coredrv.c:56: error: expected &#8216;)&#8217; before string constant
coredrv.c:59: error: &#8216;KERN_ALERT&#8217; undeclared (first use in this function)
coredrv.c:59: error: expected &#8216;)&#8217; before string constant
coredrv.c:64: error: expected &#8216;)&#8217; before string constant
coredrv.c:76: error: expected &#8216;)&#8217; before string constant
coredrv.c:86: error: expected &#8216;)&#8217; before string constant
coredrv.c:96: error: expected &#8216;)&#8217; before string constant
coredrv.c:106: error: expected &#8216;)&#8217; before string constant
coredrv.c:117: error: expected &#8216;)&#8217; before string constant
coredrv.c: In function &#8216;init_module&#8217;:
coredrv.c:127: warning: implicit declaration of function &#8216;printk&#8217;
coredrv.c: In function &#8216;hamdelay&#8217;:
coredrv.c:138: warning: implicit declaration of function &#8216;mdelay&#8217;
make[1]: *** [coredrv.o] Error 1
make[1]: Leaving directory `/home/mbnoimi/Desktop/CNet/Modem/Linux/release/src/hamcore'
make: *** [all] Error 2


```

---

