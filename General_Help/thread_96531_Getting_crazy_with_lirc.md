---
title: "Getting crazy with lirc"
date: 2005-11-29
forum: General Help
---

### Post by skop on 2005-11-29
Hi to all,

I followed all instructions on lirc in the forum, studied the lir.org site, mythtv, freevo etc tricks... But lirc still don't work.

I have a hauppauge 350, everywhere writed the best for MythTV and Freevo... And Ubuntu 5.10.

This is thee 3rd time I start over, but nothing to do. The last orror message are:

#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################


Or, in deep:

/usr/src/modules/lirc/drivers/lirc_i2c/../../drivers/kcompat.h:136:2: #error "LIRC modules currently require"
/usr/src/modules/lirc/drivers/lirc_i2c/../../drivers/kcompat.h:137:2: #error "  'Loadable module support  --->  Module unloading'"
/usr/src/modules/lirc/drivers/lirc_i2c/../../drivers/kcompat.h:138:2: #error "to be enabled in the kernel"

I'm going to became crazy! :confused: 

Regards,
JS

---

