---
title: "Toshiba SD card reader not working"
date: 2008-07-12
forum: Hardware
---

### Post by daehenoc on 2008-07-12
Hi all,

I have a Toshiba Tecra M2 with Heron installed.  Working great, except the SD card reader :(

Output from **lspci**:
```
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
```

When I plug an SD card in (which works in another card reader in another computer), nothing happens.  A search around for other similar problems has informed me about the wbsd module, I tried this and didn't have any luck - modprobe wbsd gave the correct messages in dmesg, but once wbsd is loaded, still no luck plugging an SD card in, no dmesg updates or a mounted card.

Any suggestions?

Thanks,
Greg

---

### Post by daehenoc on 2008-07-12
(dusts hands)

Hah, well Google is my friend, putting "ubuntu Toshiba America Info Systems SD TypA Controller" in, brought up this link:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/88863](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/88863)

As of Feb/Mar '08, there is still no hardware driver in Linux for this SD controller, fingers crossed for the next major kernel release!

---

### Post by krustybaguette on 2010-04-28
> **daehenoc said:**
> (dusts hands)

Hah, well Google is my friend, putting "ubuntu Toshiba America Info Systems SD TypA Controller" in, brought up this link:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/88863](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/88863)

As of Feb/Mar '08, there is still no hardware driver in Linux for this SD controller, fingers crossed for the next major kernel release!

Running Ubuntu 10.4 Lucid Lynx and have installed disk utility to see if it would pick up built in SD card reader. Nope.

As of April 2010 built-in SD card reader still not working in my Toshiba Satellite 2455-S305. Will try above link to see if the link is still working and if anything new has been discovered!

kb

---

### Post by koanhead on 2012-08-04
This thread is duplicated here:

[http://ubuntuforums.org/showthread.php?t=1581734](http://ubuntuforums.org/showthread.php?t=1581734)

I'm working on this issue right now, and I've left some information there. Any assistance would be appreciated if there are any driver hackers out there.

---

