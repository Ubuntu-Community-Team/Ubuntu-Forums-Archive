---
title: "ATI issues - how to use radeonhd driver?"
date: 2009-05-25
forum: Hardware
---

### Post by some_name on 2009-05-25
I should just point out that I am very new to Linux and Ubuntu.

I have a laptop with ATI Radeon X1250 on-board graphics, and am experiencing some issues in 9.04 such as flickering and glitching. 

A suggested solution I have come across in a number of places is to use the radeonhd driver.

An example of someone using this solution is here (comment at bottom of page - by kyosan - he/she also has X1250):

[http://blogs.computerworld.com/the_ubuntu_and_ati_blues?page=3](http://blogs.computerworld.com/the_ubuntu_and_ati_blues?page=3)

 I have yet to find anywhere that actually tells me how to set this up though - if anyone could explain how to do this, or point me in the direction of a tutorial, I would be very grateful.

Many thanks.

---

### Post by some_name on 2009-05-25
Just giving this a cheeky bump.

---

### Post by some_name on 2009-05-25
I found out that Ubuntu reverts to the radeon driver if fglrx is uninstalled.  I attempted to uninstall it in recovery mode:

```
sudo apt-get remove xorg-driver-fglrx
```It wasn't installed anyway, so I guess that means I was using the radeon driver anyway.

---

### Post by some_name on 2009-05-25
OK. Problem fixed - followed the instructions here:

[http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261](http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261)

Now there are no glitches or flickers + effects seem to be working OK as well. Nice.

---

