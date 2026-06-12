---
title: "DD9000 DVB-T driver install"
date: 2011-01-09
forum: Hardware
---

### Post by x53x6ex69x67x67x65x72 on 2011-01-09
Hi
I have a "BM Global" DD9000 USB DVB-T receiver.
It's manual says it is supported after kernel 2.6.21 by linux. 
I can't find its firmwar/driver!!
How can I install it? 
Here is my lsusb:
```
Bus 008 Device 002: ID 147e:1000 Upek 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 187f:0201  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I think "187f:0201" is the device.

---

### Post by IcarusR on 2011-01-09
Found this which may help you..

[http://arcierisinasce.wordpress.com/2010/02/21/smscore_set_device_mode-error-2-loading-firmware-dvb_nova_12mhz_b0-inp/]("http://arcierisinasce.wordpress.com/2010/02/21/smscore_set_device_mode-error-2-loading-firmware-dvb_nova_12mhz_b0-inp/")

---

### Post by x53x6ex69x67x67x65x72 on 2011-01-09
> **IcarusR said:**
> Found this which may help you..

[http://arcierisinasce.wordpress.com/2010/02/21/smscore_set_device_mode-error-2-loading-firmware-dvb_nova_12mhz_b0-inp/](http://arcierisinasce.wordpress.com/2010/02/21/smscore_set_device_mode-error-2-loading-firmware-dvb_nova_12mhz_b0-inp/)

yes worked.
Thanks

---

### Post by IcarusR on 2011-01-09
Glad to help.

Please mark the thread as 'Solved' from the 'Thread Tools' menu.

---

