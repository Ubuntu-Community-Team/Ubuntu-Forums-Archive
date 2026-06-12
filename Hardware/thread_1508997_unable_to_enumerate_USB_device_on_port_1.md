---
title: "unable to enumerate USB device on port 1"
date: 2010-06-13
forum: Hardware
---

### Post by vish91 on 2010-06-13
Hi,

I've been using Ubuntu 9.10(x86-64) ever since it got released on my Compaq Presario V3749AU Laptop with no problems but recently I'm facing an irritating problem. 

Basically syslog and kern.log logs these messages continuously.

```
Jun 14 06:10:52 vishesh-laptop kernel: [  871.110059] hub 4-0:1.0: unable to enumerate USB device on port 1
Jun 14 06:10:52 vishesh-laptop kernel: [  871.390055] hub 2-0:1.0: unable to enumerate USB device on port 1
Jun 14 06:10:53 vishesh-laptop kernel: [  871.650056] hub 4-0:1.0: unable to enumerate USB device on port 1
Jun 14 06:10:53 vishesh-laptop kernel: [  871.930049] hub 2-0:1.0: unable to enumerate USB device on port 1
Jun 14 06:10:53 vishesh-laptop kernel: [  872.190062] hub 4-0:1.0: unable to enumerate USB device on port 1
...
...
...

``` 

My internal Webcam, Wireless+Bluetooth card and all my USB ports are perfectly working. I reinstalled Ubuntu 9.10, tried Ubuntu 10.04 LTS but same problems shows up. The full screen terminals that I get by pressing CTRL+ALT+F[1-6] are unusable as they are continuously being bloated by these messages.

Is this is a hardware problem or kernel related problem? If I continue to use Ubuntu with these error message, is it safe? Will my hardware be affected?

---

### Post by rbmdi on 2010-07-06
I am having the same issue. 10.04 LTS, all usb devices seem to be working as expected, but logs and all tty's (other than 7) are flooded with constant "Unable to enumerate USB device on port 1". Any help or advice? 

lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I'm happy to provide any more info that may help...
Thanks,
RB

---

