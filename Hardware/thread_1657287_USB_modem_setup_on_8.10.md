---
title: "USB modem setup on 8.10"
date: 2011-01-01
forum: Hardware
---

### Post by luminiscence on 2011-01-01
I am trying to setup a 3G usb-based external modem on my laptop, and I am running into some problems. I have looked a lot on the net, and I have done everything that has been suggested, but still no luck. Here are some things that I have tried.

I plug in the modem, and do lsusb:
> 
Bus 005 Device 006: ID 12d1:1446 Huawei Technologies Co., Ltd.


Then I set up the nodes /dev/ttyUSB*.
> 
sudo mknod /dev/ttyUSB0 c 188 0
sudo mknod /dev/ttyUSB1 c 188 1


Then I use the usbserial driver.

> 
sudo modprobe usbserial vendor=0x12d1 product=0x1446


I have also tried using the usb_modeswitch package.

> 
sudo usb_modeswitch -v 0x12d1 -p 0x1446 -H -W
,

which gives me this message:
> 
Accessing device 006 on bus 005 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using endpoints 0x08 (out) and 0x87 (in)
Using endpoints 0x08 (out) and 0x87 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached


And then when I try to do wvdialconf, I end up with this error message:

> 
Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   USB0 USB1 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?
.

I am clueless to what to do to make it work. Can someone give me some pointers? Thanks.

---

### Post by Joe of loath on 2011-01-01
Well, your first course of action is to upgrade to something that's supported. 8.10 is old, and your modem will probably work 'out of the box' with a newer version of Ubuntu.

---

### Post by luminiscence on 2011-01-01
It does work out-of-the-box for newer versions, but for different reasons, upgrade on this particular system has not been easy to do, but thats a different matter ... I am just trying to cling on for as long as possible, then I'll just do a fresh installation.

Apart from that, seeing as how the device is being detected properly, the only problem is to make the system recognize that the usb device is a modem.

---

