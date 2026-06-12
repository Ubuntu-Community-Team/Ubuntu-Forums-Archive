---
title: "Vaio TX: 8.04 &amp; cd eject button stopped working"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by quini on 2008-04-07
Hi,

I've upgraded to 8.04 beta from Gutsy with, apparently, no problem.

I've now found that the eject key no longer provides a keycode, as it did with gutsy's kernel; I've used xev to check it.

Any idea on what to do?  Here's the information modprobing sony-laptop & sonypi provide:

```
[ 4047.940469] sony-laptop: Sony Programmable IO Control Driver v0.5.
[ 4047.940485] sony-laptop: detected Type3 model
[ 4047.946397] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:28/SNY6001:00/input/input20
[ 4047.974507] input: Sony Vaio Jogdial as /devices/virtual/input/input21
[ 4048.003156] sony-laptop: device allocated minor is 63
[ 4048.006693] sony-laptop: Sony Notebook Control Driver v0.5.
[ 4092.887248] sonypi: Sony Programmable I/O Controller Driver v1.26.
[ 4092.887361] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
[ 4092.887453] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[ 4092.887461] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[ 4092.887465] sonypi: device allocated minor is 63
[ 4092.887560] input: Sony Vaio Jogdial as /devices/platform/sonypi/input/input22
[ 4092.912630] input: Sony Vaio Keys as /devices/platform/sonypi/input/input23
[ 4164.911328] sony-laptop: Sony Notebook Control Driver v0.5.
[ 4164.913713] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:28/SNY5001:00/input/input24
[ 4164.939103] input: Sony Vaio Jogdial as /devices/virtual/input/input25
```

TIA  ;)

---

