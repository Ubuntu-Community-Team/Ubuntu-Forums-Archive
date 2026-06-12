---
title: "hdparm and S-ATA drive"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by IdoMcFly on 2005-03-22
I was wondering if hdparm has some effect on a Serial Ata drive ?

because I get this : 
```
sudo hdparm /dev/sda
/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 10011/255/63, sectors = 82348277760, start = 0
```

The 16-bit IO_support doesn't appear normal to me, is should be 32-bit, shouldn't it?

but ```
hdparm -c 1 /dev/sda
``` does not work.

---

### Post by Bob D. on 2005-03-28
Don't know if it is a typo or not, but the command should be:

```
# hdparm -c1 /dev/sda
```

NOT

```
# hdparm -c 1 /dev/sda
```

For reference you can get more info [here.](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance#32-bit_IO_SUPPORT_-c) 

I also do not know if this will even work with SATA HD's, but it can't hurt to try.  ;-) 

Bob

---

