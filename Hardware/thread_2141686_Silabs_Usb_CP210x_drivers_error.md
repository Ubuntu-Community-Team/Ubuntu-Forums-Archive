---
title: "Silabs Usb CP210x drivers error"
date: 2013-05-03
forum: Hardware
---

### Post by dali1985 on 2013-05-03
[COLOR=#000000][FONT=Arial]I have a problem when I try to install a driver for my Silabs USB to UART bridge.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I downloaded the driver from here:[http://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx](http://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm trying to install it in my raspberry which has kernel 3.6.11[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]In the instructions I can see the following:[/FONT][/COLOR]

make (your cp2010x driver)
cp cp2010x.ko to /libmodules/<kernel>/kernel/driver/usb/serial
insmod /libmodules/<kernel>/kernel/driver/usb/serial/usbserial.ko
insmod xp2010x.ko[COLOR=#000000][FONT=Arial]However,
 I get this error when I try to call MAKE:[/FONT][/COLOR]

root@raspberrypi:/home/pi/Desktop/vcp/Linux1# make
make -C /lib/modules/3.6.11+/build M=/home/pi/Desktop/vcp/Linux1 modules
make[1]: Entering directory `/usr/src/linux' 
 CC [M]  /home/pi/Desktop/vcp/Linux1/cp210x.o
/home/pi/Desktop/vcp/Linux1/cp210x.c:164:12: error: ´usb_serial_probe´ undeclared here (not in a function)
/home/pi/Desktop/vcp/Linux1/cp210x.c:165:16: error: ´usb_serial_disconnect´ undeclared here (not in a function)
/home/pi/Desktop/vcp/Linux1/cp210x.c: In function ´cp210x_init´:
/home/pi/Desktop/vcp/Linux1/cp210x.c:989:2: error: implicit declaration of function ´usb_serial_register´ [-Werror=implicit-function-declaration]
/home/pi/Desktop/vcp/Linux1/cp210x.c:996:3: error: implicit declaration of function ´usb_serial_deregister´ [-Werror=implicit-function-declaration]
[COLOR=#000000][FONT=Arial]cc1: some warnings being treated as errors
[FONT=Consolas]make[2]: *** [/home/pi/Desktop/vcp/Linux1/cp210x.o] Error 1
[/FONT][FONT=Consolas]make[1]: *** [_module_/home/pi/Desktop/vcp/Linux1] Error 2
[/FONT][FONT=Consolas]make[1]: Leaving directory `/usr/src/linux'
[/FONT][FONT=Consolas]make: *** [all] Error 2[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
What is the problem here?[/FONT][/COLOR]

---

### Post by dali1985 on 2013-05-05
any ideas??

---

