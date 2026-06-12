---
title: "Trouble connecting to TI-84+ with tilp2"
date: 2010-09-08
forum: Hardware
---

### Post by NearlyALaugh on 2010-09-08
Hi there,

After searching the forums I get the feeling I'm starting this topic in vain. But it's worth a shot:

I would like to transfer data between my **TI-84 Plus** and my computer using **tilp2**. Haven't had any luck so far, so I was wondering if anyone has tips on getting this to work.


Here's my setup:

_System:_
release: 10.04.1 LTS "lucid"
kernel: 2.6.32-24-generic

_tilp2:_
version: 1.13-0ubuntu2

_Calculator:_
TI-84 Plus

_Cable:_
SilverLink

_USB connection (lsusb):_
Bus 003 Device 003: ID 0451:e001 Texas Instruments, Inc. GraphLink


Once **tilp** is running and the calculator is connected and powered on, I go to "change device" and select the appropriate settings (i.e., cable: SilverLink, port: #3, calc: ti-84+). I press the magnifying glass to probe for attached devices and then press OK. The following errors come up:

> Msg: failed to open the USB device.
Cause: Check that the USB cable is plugged in and that the calculator is turned ON! Also, check libusb and usbfs for valid permissions.
System: Operation not permitted (errno = 1)> Msg: attempting to use a cable which has not been open before.
Cause: Internal error.
System: Resource temporarily unavailable (errno = 11)
I piped the program's output into a file, tilp.txt, which I have attached to this post. In addition, the following errors were sent to the terminal:```
(tilp:16218): ticables-WARNING **: usb_set_configuration (could not set config 1: Operation not permitted).


(tilp:16218): ticables-WARNING **: usb_claim_interface (could not claim interface 0: Operation not permitted).
```Any thoughts?


Thanks!

---

### Post by Zanderist on 2010-09-17
I have the same problem, mine isn't detected.

---

### Post by tbear2500 on 2013-02-23
Bump.  Not that I expect anyone to read this who wouldn't have without this post.  I have the same problem.  Did both "sudo chown -R user:users /dev/bus/usb" and creating a udev rule for the device with id 0451:e003 with MODE="666" and I still cannot connect as my user.  Connecting as root fixes most problems but I still cannot take screenshots or dump ROM, and I would like to be able to connect as my normal user.

---

