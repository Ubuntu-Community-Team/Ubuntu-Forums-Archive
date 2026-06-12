---
title: "How do I compile a driver?"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by pippy on 2007-04-20
Ubuntu is finally doing everything that my windows partition can do, sometimes even better. I am finding myself to be using it more and more.

However, my digital camera is not recognized in linux as a webcam. Someone has written a driver for the model [here]("http://royale.zerezo.com/zr364xx/") but I cannot compile it. I have tried gcc, make, make install and other things.

Can someone please compile it for me, or give me a tutorial on how to compile it?

---

### Post by vigleik on 2007-04-20
> **pippy said:**
> 
However, my digital camera is not recognized in linux as a webcam. Someone has written a driver for the model [here]("http://royale.zerezo.com/zr364xx/") but I cannot compile it. I have tried gcc, make, make install and other things.

Please post output of "make". That works for me.

---

### Post by pippy on 2007-04-21
from a make:

   Building zr364xx driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build/ SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/torleif/Desktop/zr364xx-0.71/zr364xx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/torleif/Desktop/zr364xx-0.71/zr364xx.mod.o
  LD [M]  /home/torleif/Desktop/zr364xx-0.71/zr364xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'

---

### Post by vigleik on 2007-04-21
That seems like it worked. No error messages. Now type "sudo make install" and your driver should be installed.

---

### Post by pippy on 2007-04-21
I just realized that the [http://royale.zerezo.com/zr364xx/](http://royale.zerezo.com/zr364xx/) site said i needed the Video for Linux API 2 (v4l2) to use it.

how ever i cannot find that in synatic manager or compile it.

its make is:


make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/torleif/Desktop/usbvision-0.9.8.1/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.o
/home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.c:40: error: expected ‘)’ before string constant
/home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.c:208: error: unknown field ‘name’ specified in initializer
/home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.c:208: warning: initialization from incompatible pointer type
/home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.c:209: error: unknown field ‘id’ specified in initializer
/home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.c:209: error: ‘I2C_ALGO_BIT’ undeclared here (not in a function)
/home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.c:212: error: unknown field ‘slave_send’ specified in initializer
/home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.c:213: error: unknown field ‘slave_recv’ specified in initializer
/home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.c: In function ‘i2c_usb_add_bus’:
/home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.c:226: error: ‘struct i2c_algorithm’ has no member named ‘id’
make[2]: *** [/home/torleif/Desktop/usbvision-0.9.8.1/src/i2c-algo-usb.o] Error 1
make[1]: *** [_module_/home/torleif/Desktop/usbvision-0.9.8.1/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2

---

### Post by pippy on 2007-04-22
hmmm, the device still cannot be mounted even with the driver installed

mount -a should find it amirite?

---

### Post by vinogans on 2007-08-18
well u got error make: *** [default] Error 2 , umm I am new to ubuntu but I think you should try this commands first 
sudo -i should make u root 
second make 
third sudo make install 
try it and tell me if it worked or not ... and try the webcam with ekiga just test it and see

---

