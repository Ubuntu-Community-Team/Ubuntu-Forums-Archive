---
title: "[SOLVED] MPT driver with scsi drives"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by arielUBA on 2007-07-19
Hi,

I have a dell precision 690 with 2 scsi disks working on raid
The raid controller is LSI SAS 1068 (Firmware v. 00.10.49.00).
I have problems when some application wants to write to disk. In that moment the computer get freeze and the /var/log/messages says the following:

[I]command: Write(10): 2a 00 0f 14 df 6a 00 00 08 00
[ 4055.440000] mptscsih: ioc0: task abort: FAILED (sc=f50166c0)
[ 4055.440000] mptscsih: ioc0: attempting task abort! (sc=f575fa80)
[/I]

The problems seems to be the mpt kernel module.
Does anyone have a similar problem?

$ uname -a
Linux gmartinepc 2.6.20-16-server-bigiron #2 SMP Thu Jun 7 20:29:34 UTC 2007 i686 GNU/Linux

I 'll really appreciate your help.

Thank you

---

