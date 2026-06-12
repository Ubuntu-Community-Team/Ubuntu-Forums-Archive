---
title: "smartctl does not return any info Toshiba A135-S2246"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by stchman on 2007-11-26
Hello all, I have a Toshiba A135-S2246 and I want to know if I am affected by the Ubuntu hard drive spin up and spin down thing.

I installed the smartmontools package and then tried to get info but here is what I got.

```

bob@kronos:~$ sudo smartctl -A /dev/sda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

bob@kronos:~$ smartctl -A /dev/sda
```

Is the smartmontools incompatible with the Toshiba hdds?

Thanks

---

### Post by roazena on 2007-12-01
The "-a" argument is case sensitive. Don't use "-A".

---

