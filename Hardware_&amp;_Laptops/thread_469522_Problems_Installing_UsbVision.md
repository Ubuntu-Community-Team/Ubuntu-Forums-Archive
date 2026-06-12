---
title: "Problems Installing UsbVision"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by seriousstorm85 on 2007-06-10
I have downloaded usbvision and extracted it to my home folder.

I have then opened the terminal and changed to the directory which the make file is in.

I have then typed sudo make

Following problem was shown:-

make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/hassan/usbvision/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/hassan/usbvision/src/i2c-algo-usb.o
/home/hassan/usbvision/src/i2c-algo-usb.c:45: error: expected &#8216;)&#8217; before string constant
/home/hassan/usbvision/src/i2c-algo-usb.c:219: error: unknown field &#8216;slave_send&#8217; specified in initializer
/home/hassan/usbvision/src/i2c-algo-usb.c:220: error: unknown field &#8216;slave_recv&#8217; specified in initializer
make[2]: *** [/home/hassan/usbvision/src/i2c-algo-usb.o] Error 1
make[1]: *** [_module_/home/hassan/usbvision/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2



Any advice on how to solve this is welcome.

N.B My apt-get install linux-kernel-headers  and   sudo apt-get install build-essential are up to date.

---

### Post by wieman01 on 2007-08-23
Your problem is that you have got a 2.6.20 which already contains 'usbvision'. There is no need to compile from source.

---

