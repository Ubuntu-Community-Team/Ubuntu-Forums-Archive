---
title: "KONICA MINOLTA C360 Series PCL not printing from 14.04 (Trusty)"
date: 2014-04-30
forum: Hardware
---

### Post by theunsheydenrych on 2014-04-30
HI
I am trying to to set up a KONICA MINOLTA C360 Series PCL network printer from my newly installed Ubuntu 14.04 laptop.

I found this post [http://ubuntuforums.org/showthread.php?t=1972926](http://ubuntuforums.org/showthread.php?t=1972926), that i used 2 years ago to got the printer printing.
I followed the same steps but it does not want to work. When printing the test page i get a page printed with the following.

```
Unknown device: pswrite
Unrecoverable error: undefined in .uninstallpagedevice
Operand stack:
       defaultdevice
```

I have cups version 1.7.2 on the machine, i did try some of the KONICA MINOLTA drivers that can be choosed from the list but it only chrashed/hanged the printer and i have to throw the power switch to recover. 

Thanks for any help in advance.

---

### Post by pdc on 2014-04-30
so you used post #6 here [http://ubuntuforums.org/showthread.php?t=1972926](http://ubuntuforums.org/showthread.php?t=1972926) to help you get the printer working 2yrs ago?

OpenPrinting has a page on Konica [http://www.openprinting.org/driver/Postscript-KONICA_MINOLTA](http://www.openprinting.org/driver/Postscript-KONICA_MINOLTA)               ......it may be of value

---

### Post by aikishugyo on 2014-04-30
Your subject states PCL but you describe installing a postscript driver. So what is it you want for this printer?
If pswrite is undefined, you should probably look at why that is, in your version of ghostscript.
Or see what other emulations the printer supports, and use a generic driver for that.

---

