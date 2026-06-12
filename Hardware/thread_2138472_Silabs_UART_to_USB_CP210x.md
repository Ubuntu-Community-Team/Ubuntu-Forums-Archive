---
title: "Silabs UART to USB CP210x"
date: 2013-04-24
forum: Hardware
---

### Post by swelogan on 2013-04-24
[COLOR=#000000][FONT=Arial]I'm having a problem installing a driver for my Silabs USB to UART bridge.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I download my driver from here:[http://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx](http://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm running Ubuntu 12.04 32bit Kernel Linux 3.5.0-27-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The instructions say that:[/FONT][/COLOR]

[FONT=Arial]make (your cp2010x driver)
[/FONT]cp cp2010x.ko to /libmodules/<kernel>/kernel/driver/usb/serial
insmod /libmodules/<kernel>/kernel/driver/usb/serial/usbserial.ko
insmod xp2010x.ko
[COLOR=#000000][FONT=Arial]
However, I get this error when I try to call make:[/FONT][/COLOR]

root@grace:/home/admin/Desktop/usb# make
make -C /lib/modules/3.5.0-27-generic/build M=/home/admin/Desktop/usb modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-27-generic'
  CC [M]  /home/admin/Desktop/usb/cp210x.o
/home/admin/Desktop/usb/cp210x.c:164:12: error: &#8216;usb_serial_probe&#8217; undeclared here (not in a function)
/home/admin/Desktop/usb/cp210x.c:165:16: error: &#8216;usb_serial_disconnect&#8217; undeclared here (not in a function)
/home/admin/Desktop/usb/cp210x.c: In function &#8216;cp210x_init&#8217;:
/home/admin/Desktop/usb/cp210x.c:989:2: error: implicit declaration of function &#8216;usb_serial_register&#8217; [-Werror=implicit-function-declaration]
/home/admin/Desktop/usb/cp210x.c:996:3: error: implicit declaration of function &#8216;usb_serial_deregister&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/admin/Desktop/usb/cp210x.o] Error 1
make[1]: *** [_module_/home/admin/Desktop/usb] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-27-generic'
make: *** [all] Error 2
[COLOR=#000000][FONT=Arial]
I am new to Linux. I've Googled the error a lot but I can't find any answers that works.[/FONT][/COLOR]

---

