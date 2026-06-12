---
title: "USB to serial chip won't work, SiLabs CP2102"
date: 2009-01-19
forum: Hardware
---

### Post by pullin on 2009-01-19
Hello folks. I have a programmer for a microcontrller (MSP430) that is supposed to work under linux, but right now I am stuck getting it to enumerate properly.

I'm running the 8.10 release, with the 2.6.27-9 kernel.

Inside it, there is a SiLabs CP2102 chip for the USB->Serial bridge.
When I plug it into my laptop running 8.10, it doesn't work.

With usbserial not loaded, I only get:

```

[ 2772.840106] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 2773.002229] usb 3-2: configuration #1 chosen from 1 choice
```

With usbserial loaded, I get:
```

[ 2821.738656] usbcore: registered new interface driver usbserial
[ 2821.740576] usbserial: USB Serial support registered for generic
[ 2821.740660] usbcore: registered new interface driver usbserial_generic
[ 2821.740667] usbserial: USB Serial Driver core
[ 2825.988078] usb 3-2: new full speed USB device using uhci_hcd and address 4
[ 2826.154373] usb 3-2: configuration #1 chosen from 1 choice
```

And I don't get a /dev entry for it at all.
I've tried the same thing on an older version (7.04 or something?) on my desktop, with the same result.

Loading the cp2101 driver also produces the same result. No /dev entry.


Furthermore, I downloaded the cp210x driver from SiLabs themselves. This is supposed to compile a module against the headers, but it doesn't work! It's because there were some minor changes in recent 2.6 kernels that put header files in differnet places. Specifically:

```
#include <asm/semaphore.h>
```

Causes an error, since it cannot be found. Changing that to:

```
#include <linux/semaphore.h>
```

allows the build to find the file, but it still fails with:
```

make -C /lib/modules/2.6.27-9-generic/build -I /var/tmp/silabs/rpmbuild/BUILD/cp210x-3.0.0 M=/var/tmp/silabs/rpmbuild/BUILD/cp210x-3.0.0 modules                                                                                                          
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'                                                        
  CC [M]  /var/tmp/silabs/rpmbuild/BUILD/cp210x-3.0.0/cp210x.o                                                               
In file included from /var/tmp/silabs/rpmbuild/BUILD/cp210x-3.0.0/cp210x.c:95:                                               
/var/tmp/silabs/rpmbuild/BUILD/cp210x-3.0.0/cp210x.h:709: error: unknown field ‘num_interrupt_in’ specified in initializer   
/var/tmp/silabs/rpmbuild/BUILD/cp210x-3.0.0/cp210x.h:710: error: unknown field ‘num_interrupt_out’ specified in initializer  
/var/tmp/silabs/rpmbuild/BUILD/cp210x-3.0.0/cp210x.h:710: warning: missing braces around initializer
```

Any ideas on how to get some form of the USB-Serial module to work? I know the CP2102 is a pretty esoteric bridge chip. 

But I pretty much _have_ to make this work, otherwise I have to start looking at other programmers, using some super complicated vmware setup, or something.
Of course, if a kernel dev happens to be reading this and wants to fix the SiLabs cp210x driver directly...hey...sure.


Thanks,
Andrew

---

### Post by philipMac on 2009-03-06
Andrew, did you get any joy with this? 
I am in a similar position, I have to be able to read data from this chip, same errors as you got.


hey, I solved this : see [http://ubuntuforums.org/showthread.php?p=6851047#post6851047](http://ubuntuforums.org/showthread.php?p=6851047#post6851047)

---

### Post by crazyy on 2009-07-03
Hi,

I have the same problem. Do anyone know how to solve it??. Did you Pulli find any solution for this problem??
__

---

### Post by pavelchjen on 2009-07-15
found that on another resource may be it could help
I am planning to get Transmitter for RC airplane and USB cable controller for programming  is same... 
# modprobe usbserial vendor=0x10c4 product=0x8054
Regarding that post [http://ve7mjc.com/node/13](http://ve7mjc.com/node/13)
kernel should map it to /dev/ttyUSB0

---

### Post by curley_sue on 2012-07-23
> **philipMac said:**
> Andrew, did you get any joy with this? 
I am in a similar position, I have to be able to read data from this chip, same errors as you got.


hey, I solved this : see [http://ubuntuforums.org/showthread.php?p=6851047#post6851047](http://ubuntuforums.org/showthread.php?p=6851047#post6851047)

Following the above [link]("http://ubuntuforums.org/showthread.php?p=6851047#post6851047") (and adjusting to ubuntu 12.04, see below) basically did the trick for me, on 10c4:8281 , which is a usb to serial converter found in Nanotec SMCI32-1 driver

The set of commands I used:

# get the required dependencies:
```
sudo apt-get install build-essential linux-source
cp /usr/src/linux-source-3.2.0.tar.bz2 .
bunzip2 linux-source-3.2.0.tar.bz2
tar xf linux-source-3.2.0.tar
cd linux-source-3.2.0/
```

#backup the original file
```
cp drivers/usb/serial/cp210x.c drivers/usb/serial/cp210x.c.orig

```
#add the missing device (where the description string is copied from the windows driver, I think anything would work here), as verified using diff:

```
diff drivers/usb/serial/cp210x.c drivers/usb/serial/cp210x.c.orig 

```
109d108
<         { USB_DEVICE(0x10C4, 0x8281) }, /* Nanotec Plug & Drive */

```
make oldconfig
make prepare
make scripts

```
# here I am skipping the error producing commands and go straight to the solution
```
cp /usr/src/linux-headers-3.2.0-26-generic/Module.symvers .
make -i M=./drivers/usb/serial
```

#backup the original module
```
sudo cp /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/cp210x.ko /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/cp210x.ko.orig
```

#and override using the new one:
```
sudo cp drivers/usb/serial/cp210x.ko /lib/modules/3.2.0-26-generic/kernel/drivers/usb/serial/cp210x.ko

```

I finally ran (without experiencing the problem the original post reports):
```
sudo modprobe cp210x

```
The output of dmesg:
[20125.994339] usbcore: registered new interface driver usbserial
[20125.994354] USB Serial support registered for generic
[20125.994393] usbcore: registered new interface driver usbserial_generic
[20125.994395] usbserial: USB Serial Driver core
[20126.001548] USB Serial support registered for cp210x
[20126.001578] cp210x 8-1:1.0: cp210x converter detected
[20126.116744] usb 8-1: reset full-speed USB device number 9 using uhci_hcd
[20126.260010] usb 8-1: cp210x converter now attached to ttyUSB0
[20126.260035] usbcore: registered new interface driver cp210x
[20126.260038] cp210x: v0.09:Silicon Labs CP210x RS232 serial adaptor driver

---

### Post by freerk55 on 2013-06-17
[COLOR=#333333][FONT=Ubuntu Mono]I have a CP210x device. A GPS travel recorderfro QStarz
When I connect the device on a USB port I see at command prompt with **lsusb**:
***Bus 002 Device 007: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x UART Bridge / myAVR mySmartUSB light***
So its there and recognized.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]I use the BT747 java software to read the data from the GPS device.
I know for sure that it worked nice with previous versions of Ubuntu.
I now tried it again in ver 13.04. 
The BT747 software worked. 
But no connection with the device.

But when I I started the software as **root** it worked![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]But it's not normal of course that the software must be run as root
What should be wrong?
What can I do about it?[/FONT][/COLOR]

---

