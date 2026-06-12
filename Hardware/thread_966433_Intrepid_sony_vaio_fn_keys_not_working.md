---
title: "Intrepid sony vaio fn keys not working"
date: 2008-11-01
forum: Hardware
---

### Post by jacalonzo on 2008-11-01
Did some one have a tip for fixing this problem?,

Laptop: SONY VAIO VGN-NR330FE (PCG-7132P). 2008

Ubuntu 8.10, fresh install.

When you work the FN + F5 and FN + F6, the controls appear in the sreen
but do no change screen brightness.

Apreciate help,

Monterrey, Nuevo Leon, México
.....

lion@linuxa:~$ lspci

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

....

lion@linuxa:~$ dmesg

   19.682440] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   19.684715] sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers)
[   19.688729] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   19.688739] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   19.688742] sonypi: device allocated minor is 60
[   19.689611] input: Sony Vaio Jogdial as /devices/platform/sonypi/input/input11
[   19.717632] input: Sony Vaio Keys as /devices/platform/sonypi/input/input12
[   19.809293] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
[   19.851132] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 664)
[   19.893102] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 666)
[   19.935053] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)

---

### Post by jacalonzo on 2008-11-01
Give this command:

xrandr --output LVDS --set BACKLIGHT_CONTROL native

Check this:

[https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/176888](https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/176888)

Salutes from Mexico ! ! !

LAPTOP: SONY VAIO VGN-NR330FE (PCG-7132P)
UBUNTU INTREPID
BIOS:R2060J9
KERNEL: Linux linuxa 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux

+

---

