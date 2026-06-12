---
title: "Sierra wireless MC8755"
date: 2009-09-01
forum: Hardware
---

### Post by Alexbit on 2009-09-01
Hi all,
My laptop (fujitsu-siemens AMILO Pro V3525) have an integrated GPRS/UMTS modem (Sierra Wireless model MC 8755).

In these days I need to use this modem to connect to the internet.
Unfortunately, after a few minutes (or more) of navigation, without any apparent reason, he stop to serve the pages.
The only thing I can do is to reboot the machine and connect again.

It's very boring!

It's very boring!
I've try with two sim made by different carrier with the same result.

Searching on sierra web site i've found this driver:
[http://sierrawireless.custhelp.com/app/answers/detail/a_id/500#driver_download](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500#driver_download)

When I tray to install I had the following error:

$ make
-----------------------------------------------------
Compiling  sierra.c
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/ubuser/Driver_SierraMC8755/sierra.o
/home/ubuser/Driver_SierraMC8755/sierra.c: In function ‘sierra_write’:
/home/ubuser/Driver_SierraMC8755/sierra.c:468: warning: format ‘%d’ expects type ‘int’, but argument 5 has type ‘size_t’
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/ubuser/Driver_SierraMC8755/sierra.mod.o
  LD [M]  /home/ubuser/Driver_SierraMC8755/sierra.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
-----------------------------------------------------

I've also attached two screenshot. Hope they help.
I use Ubuntu 9.04 kernel 2.6.28-15-generic 
Can some one help me?
Thank you in advance.
Ale

---

