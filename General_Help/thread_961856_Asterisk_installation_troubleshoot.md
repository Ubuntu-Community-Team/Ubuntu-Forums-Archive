---
title: "Asterisk installation troubleshoot"
date: 2008-10-28
forum: General Help
---

### Post by pinkat on 2008-10-28
Hello i'm new using ubuntu, i need to install asterisk, i've followed the instructions posted here: [https://wiki.ubuntu.com/AsteriskOnUbuntu](https://wiki.ubuntu.com/AsteriskOnUbuntu)
until step 5, then i receive this output:

/usr/src/modules/zaptel/vzaphfc/vzaphfc_main.c:24:26: error: linux/config.h: No such file or directory
/usr/src/modules/zaptel/vzaphfc/vzaphfc_main.c: In function &#8216;hfc_probe&#8217;:
/usr/src/modules/zaptel/vzaphfc/vzaphfc_main.c:1684: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
make[5]: *** [/usr/src/modules/zaptel/vzaphfc/vzaphfc_main.o] Error 1
make[4]: *** [/usr/src/modules/zaptel/vzaphfc] Error 2
make[3]: *** [_module_/usr/src/modules/zaptel] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-17-generic'
make[2]: *** [linux26] Error 2
make[2]: Leaving directory `/usr/src/modules/zaptel'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/zaptel'
make: *** [kdist_build] Error 2
BUILD FAILED!

I've got the headers in the src folder, but i don't know what is wrong.

I hope someone can help me.

---

### Post by alienprdkt on 2008-10-28
funny i was just thinking about trying this out yesturday,

here is an old how to I found within Tutorials & Tips let me know how it works out on a newer Ubuntu build...

[http://ubuntuforums.org/showthread.php?t=136785&highlight=Asterisk](http://ubuntuforums.org/showthread.php?t=136785&highlight=Asterisk)

---

