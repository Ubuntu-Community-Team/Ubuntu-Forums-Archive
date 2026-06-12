---
title: "parallel port and hardware key (dongle) problems"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by DaOane on 2007-01-12
Ubuntu 6.10, Kernel 2.6.17

Hello!

I have software which requires a hardware key. This Sentinel Super Pro dongle is attached to the parallel port but not recognised by the software. My user is member of the lp group which has read and write access for /dev/parport0 and /dev/lp0.
dmesg gives the following result:
```
$ dmesg | grep parport
[17179593.692000] parport: PnPBIOS parport detected.
[17179593.692000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[17179596.496000] lp0: using parport0 (interrupt-driven).

```

A script from a scanner-troubleshooting page gives some more information:
```
$ sudo sh ppdiag.sh
S01: parport built as module
 
S02: parport0:
S02:    modes:PCSPP
S02:    ADDR :0x378
S02:    IRQ  :7
S02:    DMA  :no DMA used
 
grep: /etc/modules.conf: No such file or directory
S03: no parport parameters
 
S10: ppdev built as module
 
S12: /dev/parport0 exists ...
S12: /dev/parport0 is readable ...
S12: /dev/parport0 is writable ...
 
successfull end ....

```

Has anybody had success with a parallel port dongle? What is possibly wrong with my port configuration? The only mode available is PCSPP. Is it possible that another mode is required. How do I change this?

Thank you for any advice,

Henning

---

### Post by DaOane on 2007-01-16
The problem was that the lp module occupied the parport0 device. The dongle works now after "rmmod lp".

---

### Post by alex_mayorga on 2008-07-13
> **DaOane said:**
> The problem was that the lp module occupied the parport0 device. The dongle works now after "rmmod lp".
DaOane,
Can you elaborate on your success? I'm trying to run a software that needs one of these LPT hardware keys under wine with no success at all.
My details:
The dongle is detected like this:
$ dmesg | grep parport
[   38.046763] parport_pc 00:08: reported by Plug and Play ACPI
[   38.046802] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   40.745390] lp0: using parport0 (interrupt-driven).

The program is a little known program called OPUS OLE 2.0.
The security part seems to be Sentinel Super Pro at [http://www.safenet-inc.com/support/tech/sentinel.asp](http://www.safenet-inc.com/support/tech/sentinel.asp)

I've installed both OPUS and Sentinel drivers under Wine with no problem at all, yet the program complaints that the hardware key is not present :(

Here's the error reported when trying to "reboot" Wine [http://rafb.net/p/EJznYM33.html](http://rafb.net/p/EJznYM33.html)

Any guidance would be immensely appreciated.

Thanks in advance.

---

