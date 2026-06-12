---
title: "HL-340 driver compile"
date: 2008-10-15
forum: General Help
---

### Post by carndog on 2008-10-15
I am trying to compile a ch341 driver that I downloaded form [http://tiagovaz.wordpress.com/2008/01/04/using-a-hl-340-usb-serial-adapter-against-2623-linux-kernel/]("http://tiagovaz.wordpress.com/2008/01/04/using-a-hl-340-usb-serial-adapter-against-2623-linux-kernel/") 
But I am running in to an error with the 'usb_driver' field.  I just can't seem to get past this no matter how much searching I do.  I am think it is a package that I have to include but not sure which.  Any help is appreciated.  Thanks


```

LKGD7F082:/home/chris/ch341_drv# make
make -C /lib/modules/2.6.18-6-ixp4xx/build SUBDIRS=/home/chris/ch341_drv modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.18-6-ixp4xx'
  CC [M]  /home/chris/ch341_drv/ch341.o
/home/chris/ch341_drv/ch341.c:267: warning: 'struct ktermios' declared inside parameter list
/home/chris/ch341_drv/ch341.c:267: warning: its scope is only this definition or declaration, which is probably not what you want
/home/chris/ch341_drv/ch341.c:320: error: unknown field 'usb_driver' specified in initializer
/home/chris/ch341_drv/ch341.c:320: warning: initialization makes integer from pointer without a cast
/home/chris/ch341_drv/ch341.c:320: error: initializer element is not computable at load time
/home/chris/ch341_drv/ch341.c:320: error: (near initialization for 'ch341_device.num_interrupt_in')
/home/chris/ch341_drv/ch341.c:326: warning: initialization from incompatible pointer type
make[2]: *** [/home/chris/ch341_drv/ch341.o] Error 1
make[1]: *** [_module_/home/chris/ch341_drv] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.18-6-ixp4xx'

```

---

### Post by carndog on 2008-10-18
bump

anyone?

---

### Post by richfiddler11 on 2009-01-21
Guess this is probably too late to be of use, but it looks you're trying to build for an ixp4xx (xscale CPU) target -- is that what you want? 

I'd guess most folks would be looking to build for x86, in which case something is amiss in your build environment. But can't assume too much.

I just happened to build the same code today on 8.04 and didn't have any problems.

---

