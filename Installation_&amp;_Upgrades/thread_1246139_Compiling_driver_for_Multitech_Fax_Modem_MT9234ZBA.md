---
title: "Compiling driver for Multitech Fax Modem MT9234ZBA"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by WolfLust on 2009-08-21
Hello all,

I'm trying to compile from src the driver for the MT9234ZBA-USB Multitech fax modem but i'm getting a lot of compilation error.

Could you please take a look at the following and advise?


buhu@buhu:~/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking os type... ok
checking kernel version... 2.6.28-11-generic
checking kernel sources... found /lib/modules/2.6.28-11-generic/build
checking usb-serial.h... found /lib/modules/2.6.28-11-generic/build/drivers/usb/serial/usb-serial.h
checking modules directory... /lib/modules/2.6.28-11-generic
configure: creating ./config.status
config.status: creating src/Makefile
buhu@buhu:~/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1$ sudo make install
make -C src install
make[1]: Entering directory `/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src'
cp -f /lib/modules/2.6.28-11-generic/build/drivers/usb/serial/usb-serial.h .
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.28-11-generic/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.o
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:86:27: error: asm/semaphore.h: No such file or directory
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:298: error: unknown field ‘owner’ specified in initializer
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:298: warning: initialization from incompatible pointer type
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:317: warning: initialization from incompatible pointer type
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:344: warning: initialization from incompatible pointer type
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c: In function ‘ti_open’:
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:690: warning: assignment from incompatible pointer type
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:764: warning: assignment from incompatible pointer type
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c: In function ‘ti_recv’:
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1426: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1426: error: ‘TTY_FLIPBUF_SIZE’ undeclared (first use in this function)
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1426: error: (Each undeclared identifier is reported only once
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1426: error: for each function it appears in.)
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1428: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1433: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1433: warning: type defaults to ‘int’ in declaration of ‘_min2’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1433: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1434: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1434: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1435: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1435: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1435: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1435: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1436: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1437: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1438: error: ‘struct tty_struct’ has no member named ‘flip’
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c: In function ‘ti_send’:
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1483: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c: In function ‘ti_restart_read’:
/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.c:1718: warning: assignment from incompatible pointer type
make[3]: *** [/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src/ti_usb_3410_5052.o] Error 1
make[2]: *** [_module_/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/buhu/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1/src'
make: *** [install] Error 2


buhu@buhu:~/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1$ uname -r
2.6.28-11-generic


buhu@buhu:~/Desktop/Linux_Install_new/mts_ti_usb-2.6-1.3.1$ sudo locate semaphore.h
/usr/include/semaphore.h
/usr/include/asm/semaphore.h
/usr/include/bits/semaphore.h
/usr/src/linux-headers-2.6.28-11/include/linux/semaphore.h
/usr/src/linux-headers-2.6.28-11/include/linux/asm/semaphore.h
/usr/src/linux-headers-2.6.28-11-generic/include/linux/semaphore.h
/usr/src/linux-headers-2.6.28-11-generic/include/linux/asm/semaphore.h
/usr/src/linux-source-2.6.28/include/linux/semaphore.h




lsusb -v (i pasted the multi-tech related part)
Bus 003 Device 003: ID 06e0:0319 Multi-Tech Systems, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x06e0 Multi-Tech Systems, Inc.
  idProduct          0x0319 
  bcdDevice            1.01
  iManufacturer           1 Texas Instruments
  iProduct                2 TUSB3410 Serial Port
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)



Please let me know if there is anything else that I can provide.

Thank you all.

---

### Post by WolfLust on 2009-08-21
Oh I'm using Ubuntu 9.04 Desktop Edition.

cat /proc/version
Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009

---

### Post by WolfLust on 2009-08-25
Any ideas please?

---

### Post by kapn on 2010-08-06
Hey there WolfLust, did you ever figure it out?  I'm faced with the same problem.

---

### Post by WolfLust on 2010-08-07
Hello kapn,

I didn't find a solution for this issue.

Sorry,

---

