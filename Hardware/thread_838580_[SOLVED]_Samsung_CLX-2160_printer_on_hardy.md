---
title: "[SOLVED] Samsung CLX-2160 printer on hardy"
date: 2008-06-23
forum: Hardware
---

### Post by loza on 2008-06-23
Hi I'm having real problems which seem to have come about since I have upgraded to Hardy. Everything kinda worked ok on gutsy.

Xsane is now saying it cannot find a scanner, although it works on a windows pc fine. I have done a

> 
sudo sane-find-scanner -q
and it gives me


> found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3425 [CLX-216x Series]) at libusb:003:002
I tried installing a fresh samsung driver but no change. When I look in the configurator there is no scanner detected...

The printer is still working fine though...

Also I did a

> sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


any ideas please?
Thanks in advance
loza

---

### Post by okkadiroglu on 2010-01-12
I am having the same problem. Help!

---

### Post by bittner on 2011-01-06
This has been reported to work for Ubuntu 10.04 LTS, and 10.10 Maverick.

See post "[HOWTO Install Samsung Unified Printer Driver]("http://ubuntuforums.org/showthread.php?p=10325540#post10325540")".

---

