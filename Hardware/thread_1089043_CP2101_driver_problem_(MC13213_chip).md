---
title: "CP2101 driver problem (MC13213 chip)"
date: 2009-03-06
forum: Hardware
---

### Post by philipMac on 2009-03-06
I have a Freescale MC13213 chip that which has a CP2101 chip to control the UART.  I need to get a /dev/ttyUSB* to work with I assume.


when I plugged it in initially dmesg said
[   99.868186] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  100.027183] usb 4-1: configuration #1 chosen from 1 choice

and there was nothing new in dev. 

So, I ran 
sudo modprobe cp2101
and dmesg comes up with :

[  300.940455] usbcore: registered new interface driver usbserial
[  300.940494] usbserial: USB Serial support registered for generic
[  300.940576] usbcore: registered new interface driver usbserial_generic
[  300.940582] usbserial: USB Serial Driver core
[  300.968522] usbserial: USB Serial support registered for cp2101
[  300.971945] usbcore: registered new interface driver cp2101
[  300.971958] cp2101: Silicon Labs CP2101/CP2102 RS232 serial adaptor driver v0.07

but still no joy. 

lsusb gives me:

Bus 004 Device 002: ID 08fd:000a Digianswer A/S 


I am not really sure how to proceed. 


I am pretty sure its a driver issue, the device works without problem in Windows. 

Any help would be *reeeeeally* appreciated. :(



edit, I was looking at 
Linux/drivers/usb/serial/cp2101.c
and I cannot find 08fd:000a in this file listed. 

Does this mean that the machine does not know that my device uses this driver?



This seems relevant, but I do I really need to recompile my kernel?

[http://ubuntuforums.org/showthread.php?t=750158](http://ubuntuforums.org/showthread.php?t=750158)




Ok, so I followed this thread, 
[http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

I got the source, 
> sudo apt-get install build-essential linux-source

copied it to home, 
> cp /usr/src/linux-source-2.6.27.tar.bz2  .
> bunzip2 linux-source-2.6.27.tar.bz2
tar xf linux-source-2.6.27.tar
cd linux-source-2.6.27/

added the line to cp2101.c

diff cp2101.c cp2101.c~ 
95d94
< 	{ USB_DEVICE(0x08fd, 0x000a) }, /* Digianswer A/S by philip */


> make oldconfig
make prepare
make scripts

and when I ran 
make M=./drivers/usb/serial
initially this happened : 


 >  WARNING: Symbol version dump /home/philip/linux-source-2.6.27/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD      drivers/usb/serial/built-in.o
  CC [M]  drivers/usb/serial/usb-serial.o
  CC [M]  drivers/usb/serial/generic.o
  CC [M]  drivers/usb/serial/bus.o
  CC [M]  drivers/usb/serial/ezusb.o
  LD [M]  drivers/usb/serial/usbserial.o
ld: no input files
make[1]: *** [drivers/usb/serial/usbserial.o] Error 1
make: *** [_module_./drivers/usb/serial] Error 2

(In case anyone is wondering this error is not from my messing about, it happens with the source as is. )

so, I cp'd over that file. 
cp /usr/src/linux-headers-2.6.27-11-generic/Module.symvers .

but still same problem, 

> linux-source-2.6.27$ make M=./drivers/usb/serial
  LD      drivers/usb/serial/built-in.o
  CC [M]  drivers/usb/serial/usb-serial.o
  CC [M]  drivers/usb/serial/generic.o
  CC [M]  drivers/usb/serial/bus.o
  CC [M]  drivers/usb/serial/ezusb.o
  LD [M]  drivers/usb/serial/usbserial.o
ld: no input files
make[1]: *** [drivers/usb/serial/usbserial.o] Error 1
make: *** [_module_./drivers/usb/serial] Error 2



Edit: 
so, I tried again to compile, and I just told make to ignore errors, and proceed. 

> make -i M=./drivers/usb/serial

then I backed up my old cp2101.ko file to cp2101.ko.old,
> cp drivers/usb/serial/cp2101.ko to cp2101.ko.old


and finally 

> sudo cp drivers/usb/serial/cp2101.ko /lib/modules/2.6.27-11-generic/kernel/drivers/usb/serial/cp2101.ko

the first time it didn't like the module, and gave out to me when I tried to load it via modprobe, but, I tried again and

tadaaa it worked.  It dynamically picks up the device when I plug it in and everything now. 

> [   98.664154] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   98.827045] usb 4-1: configuration #1 chosen from 1 choice
[   98.960995] usbcore: registered new interface driver usbserial
[   98.961698] usbserial: USB Serial support registered for generic
[   98.962407] usbcore: registered new interface driver usbserial_generic
[   98.962413] usbserial: USB Serial Driver core
[   99.000090] usbserial: USB Serial support registered for cp2101
[   99.003279] cp2101 4-1:1.0: cp2101 converter detected
[   99.116184] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[   99.260949] usb 4-1: cp2101 converter now attached to ttyUSB0
[   99.262002] usbcore: registered new interface driver cp2101
[   99.262011] cp2101: Silicon Labs CP2101/CP2102 RS232 serial adaptor driver v0.07



oh yeah, finally, you have to set the baud rate properly at both ends. 
> sudo stty -F /dev/ttyUSB0 speed 38400

for some reason you need to tell linux this twice before it gets the message.  The first time it tries it ignore you and doesn't change the baud rate, the second time it gives in and changes it. 

Viola.

---

### Post by johnnyjuan on 2009-04-12
Hi,

I just want to thank you for sharing this it helped me out. Just a small note for beginners as me which can prevent of spending some more time...after you replace the .ko it wont work unless you remove the module modprobe -r cp2101 and load it again modprobe cp2101.

Thank you!!

---

### Post by philipMac on 2009-04-16
oops. did I not include that step?  Heh. 

Emm, so I contacted the guy who wrote this, informed him of the fix, and he got back to me saying he will add it to the cp2101 driver source and submit it.

---

### Post by johnnyjuan on 2009-04-30
Ok, well....actually it is a kind of general method that you found for fixing devices using the chip that are not included in the driver.....I can provide the line for mine: { USB_DEVICE(0x04CC, 0x1521) } it is an Arygon NFC reader.

Thank you again

---

### Post by curley_sue on 2012-07-23
Thanks a lot philipMac!

Your solution was quick and well explained!
Following the above (and adjusting to ubuntu 12.04, see below) basically did the trick for me, on 10c4:8281 , which is a usb to serial converter found in Nanotec SMCI32-1 driver

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

### Post by aeroaks on 2012-08-04
I followed the steps you gave but I am not getting any output for "sudo modprobe cp210x"

Can anyone help?

---

### Post by takobaba on 2013-05-03
> **aeroaks said:**
> I followed the steps you gave but I am not getting any output for "sudo modprobe cp210x"

Can anyone help?


this is output of dmesg

write dmesg to your shell

cheers

---

### Post by benchapman2 on 2014-01-04
> **aeroaks said:**
> I followed the steps you gave but I am not getting any output for "sudo modprobe cp210x"

Can anyone help?



Struggling with this step too.

Does anyone have a solution?

Working in ubuntu 12.04LTS

> $ sudo modprobe cp210x
FATAL: Error inserting cp210x (/lib/modules/3.8.0-35-generic/kernel/drivers/usb/serial/cp210x.ko): Unknown symbol in module, or unknown parameter (see dmesg)



> 
$ dmesg | tail -4
[10144.018055] cp210x: Unknown symbol mcount (err 0)
[10144.018086] cp210x: Unknown symbol usb_serial_probe (err 0)
[10144.018101] cp210x: Unknown symbol usb_serial_register (err 0)
[10144.018116] cp210x: Unknown symbol usb_serial_deregister (err 0)


Thanks
Ben

---

