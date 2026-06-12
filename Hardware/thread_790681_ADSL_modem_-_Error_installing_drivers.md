---
title: "ADSL modem - Error installing drivers"
date: 2008-05-11
forum: Hardware
---

### Post by mgiaff on 2008-05-11
Hi there!

I'm trying to install an ADSL modem (provided from my ISP). The modem is called "Access Media Fastrate USB 100" and pratically corresponds to the "BeWAN ADSL USB ST". On the wiki of the Ubuntu Italian Community there's a guide ([http://wiki.ubuntu-it.org/Hardware/Modem/FastrateUsb100](http://wiki.ubuntu-it.org/Hardware/Modem/FastrateUsb100)).

You can eventually find the driver's package here: [http://www.bewan.com/bewan/drivers/A1012-A1006-A904-A888-A983-0.9.3.tgz](http://www.bewan.com/bewan/drivers/A1012-A1006-A904-A888-A983-0.9.3.tgz)

I'm following the steps, but an error occours as output of the following command:
```
make modules CC=/usr/bin/gcc-4.2
```

You have to know that I edited the command of the guide, because it is a guide for Ubuntu Dapper Drake and the gcc version used to compile the files was the 3.4. The original command was:
```
make modules CC=/usr/bin/gcc-3.4
```

I post the output of the edited command:
```

mauri@UB-Mauri:~/unicorn$ make modules CC=/usr/bin/gcc-4.2
for i in libm unicorn_pci unicorn_usb ; do make -C $i modules MODDIR=/home/mauri/unicorn/$i ; done
make[1]: Entering directory `/home/mauri/unicorn/libm'
make[1]: Nothing to be done for `modules'.
make[1]: Leaving directory `/home/mauri/unicorn/libm'
make[1]: Entering directory `/home/mauri/unicorn/unicorn_pci'
make CC=/usr/bin/gcc-4.2 -C /usr/src/linux SUBDIRS=/home/mauri/unicorn/unicorn_pci modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.o
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:7:26: error: linux/config.h: Nessun file o directory
In file included from /home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:14:
include/linux/pci.h: In function ‘pci_register_driver’:
include/linux/pci.h:631: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)
include/linux/pci.h:631: error: (Each undeclared identifier is reported only once
include/linux/pci.h:631: error: for each function it appears in.)
In file included from /home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:21:
/home/mauri/unicorn/unicorn_pci/../include/types.h: At top level:
/home/mauri/unicorn/unicorn_pci/../include/types.h:33: error: conflicting types for ‘bool’
include/linux/types.h:33: error: previous declaration of ‘bool’ was here
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c: In function ‘start_device’:
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:986: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:986: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c: At top level:
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2160: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2162: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2163: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2165: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2166: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2168: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2170: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2171: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2172: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2173: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2174: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2175: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2176: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2177: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2178: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2181: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2186: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.c:2191: error: expected ‘)’ before string constant
make[3]: *** [/home/mauri/unicorn/unicorn_pci/unicorn_pcidrv.o] Error 1
make[2]: *** [_module_/home/mauri/unicorn/unicorn_pci] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/mauri/unicorn/unicorn_pci'
make[1]: Entering directory `/home/mauri/unicorn/unicorn_usb'
make CC=/usr/bin/gcc-4.2 -C /usr/src/linux SUBDIRS=/home/mauri/unicorn/unicorn_usb modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.o
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:7:26: error: linux/config.h: Nessun file o directory
In file included from /home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:15:
include/linux/usb.h: In function ‘usb_register’:
include/linux/usb.h:1013: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)
include/linux/usb.h:1013: error: (Each undeclared identifier is reported only once
include/linux/usb.h:1013: error: for each function it appears in.)
In file included from /home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:21:
/home/mauri/unicorn/unicorn_usb/../include/types.h: At top level:
/home/mauri/unicorn/unicorn_usb/../include/types.h:33: error: conflicting types for ‘bool’
include/linux/types.h:33: error: previous declaration of ‘bool’ was here
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c: In function ‘dump_urb’:
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:124: error: ‘struct urb’ has no member named ‘bandwidth’
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c: In function ‘fill_isoc_urb’:
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:144: error: ‘struct urb’ has no member named ‘lock’
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c: In function ‘StartAtmUsXfer’:
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:420: warning: passing argument 7 of ‘fill_isoc_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:425: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c: In function ‘atm_start_rcv’:
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:554: warning: passing argument 7 of ‘fill_isoc_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:560: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c: In function ‘start_device’:
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:1236: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c: In function ‘USB_S_Write’:
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:1639: warning: passing argument 7 of ‘fill_isoc_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:1646: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c: In function ‘USB_L_Write’:
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:1711: warning: passing argument 7 of ‘fill_isoc_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:1720: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c: In function ‘USB_Read’:
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:1798: warning: passing argument 7 of ‘fill_isoc_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:1806: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:1825: warning: passing argument 7 of ‘fill_isoc_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:1832: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c: At top level:
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2292: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2294: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2295: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2297: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2298: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2299: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2300: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2301: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2302: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2303: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2304: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2305: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2306: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2307: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2308: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2309: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2311: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2313: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2314: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2315: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2317: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2318: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2320: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2321: error: expected ‘)’ before string constant
/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.c:2324: error: expected ‘)’ before string constant
make[3]: *** [/home/mauri/unicorn/unicorn_usb/unicorn_usbdrv.o] Error 1
make[2]: *** [_module_/home/mauri/unicorn/unicorn_usb] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/mauri/unicorn/unicorn_usb'
make: *** [modules] Error 2

```

The first error of this output regards the file **linux/config.h**...

Perhaps it's useful to know that I have Ubuntu Hardy Heron (I updated the packages this afternoon, so everything should be at the last version available).


Thanks a lot!
Mauri


P.S.: Sorry for my very bad English. If you need other details just ask!

---

### Post by mgiaff on 2008-05-11
Up :)

---

### Post by mgiaff on 2008-05-12
None? :(

---

