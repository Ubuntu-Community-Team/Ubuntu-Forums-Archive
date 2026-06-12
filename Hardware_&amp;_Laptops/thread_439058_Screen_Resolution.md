---
title: "Screen Resolution"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by Keithod on 2007-05-10
Hi just installed Ubuntu Feisty Fawn on my new Compaq presario C542ea and the resolution is a little below what it should be. It makes the screen look rather unattractive and blurry! I have tried changing the resolution in the system menu but the max resolution offered is 1024 x 768, I need 1280x800. is there anything I can do?

I'm also having trouble with my wireless card but one step at a time perhaps [the card can pick up the wireless network but wont connect....I tried with encryption switched off too.].

I had mandriva on the machine last week and the resolution was perfect. ..

Any help greatly appreciated.

Kind regards,
Keith

---

### Post by Maylar on 2007-05-10
what vid card is in the system? And, what driver do you have installed?

---

### Post by Keithod on 2007-05-10
It's an Intel 945GM card. To be honest, I'm not sure what driver is installed for it. How can I check?

Thank you for your reply.

---

### Post by jjordan on 2007-05-10
This may be the most common issue on this forum, search for i915resolution and you will find several threads on fixing this issue and even a howto or two.

In short:
Install i915resolution
reboot to see if it autodetects your screen and sets the resolution you want.
If not set XRESO and YRESO in /etc/default/915resolution manually
restart x or reboot

- j

---

### Post by Keithod on 2007-05-11
Thanks mate!  I'll try that and let you know, many thanks!

---

### Post by Keithod on 2007-05-12
Hi I have tried installing i915 resolution and the following pops up:

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.




The log is as follows:

make DRM_MODULES=i915.o modules
make[1]: Entering directory `/home/keith/Desktop/i915/drm/linux-core'
make -C /lib/modules/2.6.20-15-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/keith/Desktop/i915/drm/linux-core/drm_auth.o
In file included from /home/keith/Desktop/i915/drm/linux-core/drm_auth.c:36:
/home/keith/Desktop/i915/drm/linux-core/drmP.h:44:26: error: linux/config.h: No such file or directory
make[3]: *** [/home/keith/Desktop/i915/drm/linux-core/drm_auth.o] Error 1
make[2]: *** [_module_/home/keith/Desktop/i915/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/keith/Desktop/i915/drm/linux-core'
make: *** [i915.o] Error 2

Any suggestions, please.

Thanks again.

---

