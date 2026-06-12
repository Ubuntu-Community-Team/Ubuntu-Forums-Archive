---
title: "Failing to install Monoprice pen monitor driver"
date: 2022-10-13
forum: Hardware
---

### Post by MZ250Supa5 on 2022-10-13
For the past five years I've been using a Parblo Coast 22 pen monitor which has worked well on Ubuntu using the Monoprice 22 driver, (essentially the Monoprice and Parblo are the same product). I've had the odd difficulty as things have changed but these have been relatively easily solved after having posted the issue here on the forums, which is what I'm doing again now.

All the essential dependencies are installed, such as libusb-1.0-0 as is pkg-config but I still get this result:

```
padi@moron:~/Monoprice_22_linux_kernel_module-master$ make
gcc detach_usbhid.c -I/usr/include/libusb-1.0  -L/lib/-linux-gnu/libusb-1.0.so.0 -lusb-1.0 -o detach_usbhid
detach_usbhid.c:3:10: fatal error: libusb.h: No such file or directory
    3 | #include <libusb.h>
      |          ^~~~~~~~~~
compilation terminated.
make: *** [Makefile:10: all] Error 1

```

I'm stumped, so would appreciate some pointers.

---

### Post by Holger_Gehrke on 2022-10-14
For compiling from source you don't just need the library, you also need the header files which tell the compiler what functions are in the library. Those headers are typically found in packages named the same as the package for the library but with '-dev' appended for example 'libusb-dev'.

Holger

---

### Post by MZ250Supa5 on 2022-11-19
Thanks Holger. I've added the required headers and achieved some progress , but the driver still isn't installing. The output I get is thus:

```
padi@moron:~$ cd Monoprice_22_linux_kernel_module-master/
padi@moron:~/Monoprice_22_linux_kernel_module-master$ make
gcc detach_usbhid.c -I/usr/include/libusb-1.0  -L/lib/-linux-gnu/libusb-1.0.so.0 -lusb-1.0 -o detach_usbhid
make -C /lib/modules/5.15.0-53-generic/build M=/home/padi/Monoprice_22_linux_kernel_module-master modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-53-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: gcc (Ubuntu 11.2.0-19ubuntu1) 11.2.0
  You are using:           gcc (Ubuntu 11.3.0-1ubuntu1~22.04) 11.3.0
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-53-generic'
padi@moron:~/Monoprice_22_linux_kernel_module-master$ sudo make install
[sudo] password for padi: 
cp ./mono_22.ko /lib/modules/5.15.0-53-generic/kernel/drivers/input/tablet/
echo mono_22 >> /etc/modules
depmod
cp ./load_mono_22.sh /usr/local/bin
cp ./detach_usbhid /usr/local/bin
cp ./load_mono_22.rules /etc/udev/rules.d
/bin/udevadm control --reload
modprobe mono_22
modprobe: ERROR: could not insert 'mono_22': Exec format error
make: *** [Makefile:28: install] Error 1
padi@moron:~/Monoprice_22_linux_kernel_module-master$

```

Checking the error with a web search revealed that secure boot may be affecting the install, so I disabled secure boot, but got the same result. I'm at the point now when I'm considering rolling back my system to 20.04 as I at least know that it all works under that earlier version.

---

