---
title: "msp430 usb jtag programmer on 8.04"
date: 2008-05-16
forum: Hardware
---

### Post by itsmitty on 2008-05-16
I'm trying to get my msp-fet430uif (usb jtag programmer) to work under hardy.  So far I've tried recompiling the kernel module a few times with various patches with no luck.  Some sites have suggested this step...

# echo 2 > /sys/bus/usb/devices/2-1/bConfigurationValue 

Where 2-1 is the port identified in dmesg.  However the default permissions on that file are 0644, but attempting to echo 2 to the file returns invalid argument(see below).

I know the device works under windows.  Any ideas?

```

--- dmesg ---

[   81.438497] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   81.635229] usb 2-1: configuration #1 chosen from 1 choice
[   81.764553] usbcore: registered new interface driver usbserial
[   81.764928] /home/ian/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   81.765338] usbcore: registered new interface driver usbserial_generic
[   81.765345] /home/ian/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   81.781928] /home/ian/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 3410 1 port adapter
[   81.781962] /home/ian/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 5052 2 port adapter
[   81.782011] ti_usb_3410_5052: probe of 2-1:1.0 failed with error -5
[   81.782026] usbcore: registered new interface driver ti_usb_3410_5052
[   81.782031] /home/ian/linux-2.6.24/drivers/usb/serial/ti_usb_3410_5052.c: TI USB 3410/5052 Serial Driver v0.9

--- /sys ---

/sys/bus/usb/devices/2-1$ ls -la
total 0
drwxr-xr-x 5 root root     0 2008-05-16 08:44 .
drwxr-xr-x 6 root root     0 2008-05-16 08:44 ..
drwxr-xr-x 4 root root     0 2008-05-16 08:44 2-1:1.0
-rw-r--r-- 1 root root  4096 2008-05-16 08:44 authorized
-r--r--r-- 1 root root  4096 2008-05-16 08:44 bcdDevice
-rw-r--r-- 1 root root  4096 2008-05-16 08:44 bConfigurationValue
-r--r--r-- 1 root root  4096 2008-05-16 08:44 bDeviceClass
-r--r--r-- 1 root root  4096 2008-05-16 08:44 bDeviceProtocol
-r--r--r-- 1 root root  4096 2008-05-16 08:44 bDeviceSubClass
-r--r--r-- 1 root root  4096 2008-05-16 08:44 bmAttributes
-r--r--r-- 1 root root  4096 2008-05-16 08:44 bMaxPacketSize0
-r--r--r-- 1 root root  4096 2008-05-16 08:44 bMaxPower
-r--r--r-- 1 root root  4096 2008-05-16 08:44 bNumConfigurations
-r--r--r-- 1 root root  4096 2008-05-16 08:44 bNumInterfaces
-r--r--r-- 1 root root  4096 2008-05-16 08:44 busnum
-r--r--r-- 1 root root  4096 2008-05-16 08:44 configuration
-r--r--r-- 1 root root 65553 2008-05-16 08:44 descriptors
-r--r--r-- 1 root root  4096 2008-05-16 08:44 dev
-r--r--r-- 1 root root  4096 2008-05-16 08:44 devnum
lrwxrwxrwx 1 root root     0 2008-05-16 08:44 driver -> ../../../../../bus/usb/drivers/usb
lrwxrwxrwx 1 root root     0 2008-05-16 08:44 ep_00 -> ../../../../../devices/pci0000:00/0000:00:1a.1/usb2/2-1/usb_endpoint/usbdev2.2_ep00
-r--r--r-- 1 root root  4096 2008-05-16 08:44 idProduct
-r--r--r-- 1 root root  4096 2008-05-16 08:44 idVendor
-r--r--r-- 1 root root  4096 2008-05-16 08:44 manufacturer
-r--r--r-- 1 root root  4096 2008-05-16 08:44 maxchild
drwxr-xr-x 2 root root     0 2008-05-16 08:44 power
-r--r--r-- 1 root root  4096 2008-05-16 08:44 product
-r--r--r-- 1 root root  4096 2008-05-16 08:44 quirks
-r--r--r-- 1 root root  4096 2008-05-16 08:44 serial
-r--r--r-- 1 root root  4096 2008-05-16 08:44 speed
lrwxrwxrwx 1 root root     0 2008-05-16 08:44 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2008-05-16 08:44 uevent
-r--r--r-- 1 root root  4096 2008-05-16 08:44 urbnum
drwxr-xr-x 3 root root     0 2008-05-16 08:44 usb_endpoint
-r--r--r-- 1 root root  4096 2008-05-16 08:44 version
/sys/bus/usb/devices/2-1$ sudo su
Password or swipe finger: 
/sys/devices/pci0000:00/0000:00:1a.1/usb2/2-1# echo 2 > bConfigurationValue 
bash: echo: write error: Invalid argument

--- lsusb -v ---
Bus 002 Device 002: ID 0451:f430 Texas Instruments, Inc. MSP-FET430UIF JTAG Tool
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0451 Texas Instruments, Inc.
  idProduct          0xf430 MSP-FET430UIF JTAG Tool
  bcdDevice            1.01
  iManufacturer           1 Texas Instruments
  iProduct                2 MSP-FET430UIF JTAG Tool
  iSerial                 3 TUSB3410583B8D00655DFFB4
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

```

---

### Post by rodjer01 on 2008-06-23
dmesg:
```
[ 2863.102528] usb 5-1: new full speed USB device using uhci_hcd and address 4
[ 2863.298538] usb 5-1: configuration #1 chosen from 1 choice
[ 2863.373553] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 3410 1 port adapter
[ 2863.373751] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 5052 2 port adapter
[ 2863.373940] ti_usb_3410_5052: probe of 5-1:1.0 failed with error -5
[ 2863.374036] usbcore: registered new interface driver ti_usb_3410_5052
[ 2863.374039] /build/buildd/linux-2.6.24/drivers/usb/serial/ti_usb_3410_5052.c: TI USB 3410/5052 Serial Driver v0.9

```

google brought me to [ftp://ftp.fl.priv.at/pub/msp430/ez430-on-SuSE-10.2.txt]("ftp://ftp.fl.priv.at/pub/msp430/ez430-on-SuSE-10.2.txt") and I patched the driver the suggested way.
I also copied the udev-rule from [ftp://ftp.fl.priv.at/pub/msp430/ez430/36-MSP430-FET.rules]("ftp://ftp.fl.priv.at/pub/msp430/ez430/36-MSP430-FET.rules") to /etc/udev/rules.d. but i don't know if this rule has been invoked or not.

i'm using Ubuntu 8.04 Kernel 2.6.24-19-generic and by the way, i'm new to linux/ubuntu.

---

### Post by jcoffland on 2008-07-28
The driver patch described here worked for me.

  [http://lkml.org/lkml/2007/11/1/78](http://lkml.org/lkml/2007/11/1/78)

I have kernel version ubuntu 2.6.24-19-generic.

I installed linux-source-2.6.24

cd /usr/src
sudo tar xjvf linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24
sudo cp /boot/config-2.6.24-19-generic .config
sudo make oldconfig
# change driver as described above at lkml.org
sudo vi drivers/usb/serial/ti_usb_3410_5052.c
sudo make

sudo rmmod ti_usb_3410_5052
sudo cp rivers/usb/serial/ti_usb_3410_5052.ko /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/
sudo depmod -a

# Replug in the MSP-FET430UIF

sudo /bin/bash -c 'echo 2 >/sys/bus/usb/devices/2-2/bConfigurationValue'

Note that the 2-2 is the USB address on my system.  May be different on yours.

After all that the device is recognized and assigned to /dev/ttyUSB0.  Or a higher number.

I haven't quite figured out how to get the /etc/udev/rules.d/026_ti_usb_3410.rules file to work correctly.  Can anyone help on this.  Mine file is attached.

---

### Post by jcoffland on 2008-07-28
Ok, I solved my problem.  After following the above procedure the attached file made it work automatically.

Download the attachment and then:

cp 026_ti_usb_3410.rules.txt /etc/udev/rules.d/026_ti_usb_3410.rules

For some reason the path to bConfigurationValue for this device is different on my system (Hardy).

---

### Post by Waq on 2008-08-15
strange, whenever I punch in 
$sudo /bin/bash -c 'echo 2 >/sys/bus/usb/devices/2-2/bConfigurationValue'
I get : /bin/bash: line 0: echo: write error: Invalid argument

I am using 2.6.24-19-generic, ubuntu hardy.

I also tried recompiling the module as jcoffland earlier mentioned but to no avail. 
[edit#1: oops, it worked on a second try. I guess I was not doing sth right.]

As a solution, I recompiled latest stable (2.6.26) vanilla kernel and Jtag sarted working, though everything else (nvidia display, sound, hibernation etc..) broke down.

I would still like to use my original 2.6.24-19-generic kernel. Any suggestions on making this Jtag device run on this kernel ...
[edit#1: Now it works.]
JTAG Device I am using : MSP-FET430UIF, usb model

---

