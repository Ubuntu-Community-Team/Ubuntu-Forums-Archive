---
title: "Compatibility of Toshiba DVD-ROM SD-R6012"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by bsnimunf on 2007-03-16
I can get my DVD Drive to work with Ubuntu. Any suggestions where might i find a compatibility list or driver for the device.  if it helps my laptop is AN EASY NOTE k5285.

Any help is appreciated

---

### Post by bsnimunf on 2007-03-16
that should read can't

---

### Post by dannyboy79 on 2007-03-16
what does this output?

dmesg | grep DVD

and then also, make sure you have the correct fstab entry (great guide: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)) so that the system knows what to do when you insert a dvd. there is also a guide here that should help.

[http://crashrecovery.org/oss-dvd/HOWTO-ossdvd.html](http://crashrecovery.org/oss-dvd/HOWTO-ossdvd.html)



good luck!

---

