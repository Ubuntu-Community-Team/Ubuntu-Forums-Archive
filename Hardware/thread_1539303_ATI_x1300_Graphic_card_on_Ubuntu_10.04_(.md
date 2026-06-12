---
title: "ATI x1300 Graphic card on Ubuntu 10.04 :("
date: 2010-07-26
forum: Hardware
---

### Post by drunkuilled on 2010-07-26
Hi guys,

I googled for this problem - still couldn't solve it : can't make ati mobility radeon x1300 to get working with ubuntu 10.04. When I do fglrxinfo - get a segmentation fault.

Program received signal SIGSEGV, Segmentation fault.
0x00193ef6 in XF86DRIQueryExtension () from /usr/lib/fglrx/libGL.so.1

1. Is there a way of making this video card work? i tried a lot already - reinstalling the drivers, reconfiguring the x-server and I am pretty much exhausted now.
2. Is there a way of getting rid of the segmentation fault by using some generic graphic driver? I really need it for another software that doesn't start with the same segfault.

Cheers,
Sergey

---

### Post by P4man on 2010-07-26
the X1300 is supported out of the box afaik. I installed 10.04 on an acer with that card only days ago and everything worked just fine with the auto installed open source drivers.

You however; apparently tried to install the closed source ATI drivers; which do not support your videocard anymore. remove them, and stick to the default drivers; they work pretty well.

---

### Post by Rrogers on 2010-08-14
If you are removing the proprietary drivers; i.e. fglrx then follow the instructions in the middle of the page:  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Tedious but it seems to be necessary.
Actually you probably should at least read the whole page.  It's pretty thorough.
Ray

---

