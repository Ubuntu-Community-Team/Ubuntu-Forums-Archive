---
title: "USB Modem"
date: 2004-11-28
forum: Hardware &amp; Laptops
---

### Post by mac on 2004-11-28
Hello,

I hope that someone can help me on a problem that I have with a USB Modem, I don't really belive that it's an ubuntu issue.

I have an Intracom NetMod USB, that works without a problem on windows, and actually it did work on Linux with a 2.4 kernel, but after upgrading to ubuntu and kernel 2.6 it stop working on linux. The modem doesn't have specific drivers, it uses the ACM module, which by the way seems to be renamed to cdc_acm on 2.6 kernels.

If I cat /proc/bus/usb/devices I got:
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=02(comm.) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=0bf1 ProdID=0001 Rev= 1.00
S:  Manufacturer=Intracom S.A.
S:  Product=NetMod USB
S:  SerialNumber=Firmware Ver 1.0
C:* #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=02 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

The modem seems to be recognized by linux, but could not find which driver use (look at Driver=(none)).

Any help on this would be appreciate.

Thanks.

---

### Post by Danilo on 2005-01-08
I have a similar problem. Actually, it works for me with Ubuntu Live CD (I think it uses Linux 2.6.7, so that might be the reason), but fails on complete Ubuntu installation.

I'll look into it in more detail and report back, but with this being my only Internet-accessible machine, it might take some time.

---

### Post by Danilo on 2005-01-08
That was correct assumption. I'm posting this from Ubuntu with kernel (and modules) taken from Live CD.

This was apparently introduced in 2.6.8 kernels, and might be fixed in 2.6.10 (look at [ChangeLog-2.6.10](http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.10) and [ChangeLog-2.6.9](http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.9), entries by <oliver@neukum.org>).

---

### Post by mac on 2005-01-09
Thanks Danilo;
I will keep and eye on newer ubuntu kernels.

---

### Post by mattis on 2005-02-22
[QUOTE=mac]Thanks Danilo;
I will keep and eye on newer ubuntu kernels.[/QUOTE]

Hi,
 I have the same problem (with an elsa microlink 56k usb). Did you find a solution?
Matthias

---

### Post by mac on 2005-02-22
Mattis;

I did just updated to a newer kernel from ubuntu repository, and the modem start working.

---

