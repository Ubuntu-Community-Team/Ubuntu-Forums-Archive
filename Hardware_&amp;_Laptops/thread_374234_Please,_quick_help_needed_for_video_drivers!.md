---
title: "Please, quick help needed for video drivers!"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by sohaibma on 2007-03-02
I am trying to install openchrome drivers for my video card on edgy, following this guide:
**[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)**
(please take a look at it.)

anyway, when i came to this step
**make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via **

terminal gave me this error:

**make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via **
make -C /lib/modules/2.6.17-11-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/lib/modules/2.6.17-11-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-11-386/build'
make: *** [modules] Error 2


what is this error and how can i fix it?

---

### Post by sohaibma on 2007-03-02
i searched the forums and saw that quite a few people are facing the same problems as me, and they haven't received any useful help.

so,please anyone help me out here in any way possible

---

### Post by scxtt on 2007-03-02
do you have the kernel headers installed for your current kernel?  the build directory is a "ln -s" to them ... do a "sudo aptitude search `uname -r`"
```
[font=courier]:> ll
total 1.4M
lrwxrwxrwx  1 root root   36 2007-02-16 21:47 build -> /usr/src/linux-headers-2.6.15-28-686
drwxr-xr-x  2 root root 4.0K 2007-02-14 03:33 initrd
drwxr-xr-x 10 root root 4.0K 2007-02-14 03:33 kernel
drwxr-xr-x  2 root root 4.0K 2007-03-01 01:26 misc
-rw-r--r--  1 root root 299K 2007-03-01 01:26 modules.alias
-rw-r--r--  1 root root   69 2007-03-01 01:26 modules.ccwmap
-rw-r--r--  1 root root 304K 2007-03-01 01:26 modules.dep
-rw-r--r--  1 root root  813 2007-03-01 01:26 modules.ieee1394map
-rw-r--r--  1 root root  806 2007-03-01 01:26 modules.inputmap
-rw-r--r--  1 root root  22K 2007-03-01 01:26 modules.isapnpmap
-rw-r--r--  1 root root   74 2007-03-01 01:26 modules.ofmap
-rw-r--r--  1 root root 237K 2007-03-01 01:26 modules.pcimap
-rw-r--r--  1 root root 1.2K 2007-03-01 01:26 modules.seriomap
-rw-r--r--  1 root root 125K 2007-03-01 01:26 modules.symbols
-rw-r--r--  1 root root 354K 2007-03-01 01:26 modules.usbmap

:> aptitude search `uname -r`
Password:
i   fglrx-kernel-2.6.15-28-686                     - ATI binary kernel module for Linux 2.6.15-28-686
i   linux-headers-2.6.15-28-686                    - Linux kernel headers 2.6.15 on PPro/Celeron/PII/PIII/PIV
i   linux-image-2.6.15-28-686                      - Linux kernel image for version 2.6.15 on PPro/Celeron/PII
p   linux-restricted-modules-2.6.15-28-686         - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PI[/font]
```

---

### Post by sohaibma on 2007-03-03
I did not understand the first part of your post. The secong part shows this:

```
i   linux-headers-2.6.17-11-386                         - Linux kernel headers for version 2.6.17 on i386              
i   linux-image-2.6.17-11-386                           - Linux kernel image for version 2.6.17 on i386                
p   linux-image-debug-2.6.17-11-386                     - Linux kernel debug image for version 2.6.17 on i386          
i   linux-restricted-modules-2.6.17-11-386              - Non-free Linux 2.6.17 modules on 3866      

```


what is the problem here? can you help me please?

---

### Post by sohaibma on 2007-03-05
guys, I really need to solve this problem.
please helpme ASAP!
I'll be very thankful to you

---

### Post by scxtt on 2007-03-05
what does **glxinfo** return for you?

what release are you using (breezy, dapper, edgy, fiesty)?  that howto says 3d should work "out of the box" in edgy - are you using edgy?

also, are you sure that "Change to the correct directory (you have to already be in the directory drm)" is the case when running the command that errors out?  and are you sure "No rule to make target `modules'. Stop" means that you're not supposed to replace "modules" w/ something like "via" (tho it seems "DRM_MODULES=via" would take care of that) ...

---

### Post by sohaibma on 2007-03-06
[B]thanks scxtt for replying

glxinfo gives me this:[/B]
name of display: :0.0
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  19
  Current serial number in output stream:  19


I am using edgy, but the 3d support is not out of the box. I'm pretty sure of that.


I'm also sure that i'm in the correct directory.

can you or anyone else figure out what the problem is?

---

### Post by sohaibma on 2007-03-12
please help me out here!
i need to solve this problem otherwise i won't be able to shift from windows completely
what does the glxinfo result that i got mean?
how do i fix the problem?

---

### Post by sohaibma on 2007-03-19
please guys, I really need some help!!!


what does the glxinfo result that i got mean?
how do i fix the problem?

---

