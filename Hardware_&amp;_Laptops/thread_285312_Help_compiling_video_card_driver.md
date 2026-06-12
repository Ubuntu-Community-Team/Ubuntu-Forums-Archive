---
title: "Help compiling video card driver"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by kernco on 2006-10-26
My laptop has a VIA K8N890 video card, which doesn't appear to be supported by Ubuntu.  In my xorg.conf, it shows I have a "Generic Video Card" and it's using the vesa driver.  When I switch it to via, X doesn't start (EE No devices detected).  VIA provides a Linux driver for this card, though.  The problem is, none of the binaries are for Ubuntu or even Debian (they provide Mandriva, Fedora, Red Hat, and SuSE).  So I downloaded the source to compile it myself.  It won't compile because it is hard-coded to be built in an XFree86 environment.  They have a nice "makedriver" program which should automate everything.  Here is what it outputs:
```

 -------- Check source code --------
cp: target `/usr/src/xc/programs/Xserver/hw/xfree86/drivers/' is not a directory: No such file or directory
 -- via folder not found--------
 -- Please copy via folder into /usr/src/xc/programs/Xserver/hw/xfree86/drivers folder
```
I tried going into the source directory and running 'make' myself, and got these errors:
```

In file included from /usr/include/features.h:346,
                 from /usr/include/stdlib.h:25,
                 from via_driver.c:32:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
via_driver.c:33:21: error: xf86RAC.h: No such file or directory
via_driver.c:34:22: error: shadowfb.h: No such file or directory
via_driver.c:36:21: error: globals.h: No such file or directory
via_driver.c:38:29: error: extensions/dpms.h: No such file or directory
In file included from via_driver.c:41:
via_driver.h:36:19: error: vgaHW.h: No such file or directory
via_driver.h:37:18: error: xf86.h: No such file or directory
via_driver.h:38:27: error: xf86Resources.h: No such file or directory
via_driver.h:39:24: error: xf86_ansic.h: No such file or directory
via_driver.h:40:21: error: xf86Pci.h: No such file or directory
...
```
I didn't include all the errors here, but you get the idea.  There were a ton of headers not found, and then all the unknown identifiers because of that.

Has anyone compiled this driver in Ubuntu, or know how to compile this?  Thanks.

---

### Post by kernco on 2006-10-26
Oh, and here is a link to the source code for the driver:
[http://www.viaarena.com/Driver/k8m890xf40069-kernel-src_20060620.tgz](http://www.viaarena.com/Driver/k8m890xf40069-kernel-src_20060620.tgz)

---

