---
title: "Installing USB Wireless card"
date: 2008-05-24
forum: Hardware
---

### Post by oxsyn on 2008-05-24
I'm using Ubuntu 8.04 desktop on a Toshiba Satellite laptop.  Out of the box, Ubuntu recognized, installed & configured my integrated wireless.

I also have a Hawking USB wireless adapter.  When I plug it in, nothing happens.  When I run ifconfig, I do not see it listed (though my integrated is, obviously).

Not quite sure how to proceed.  Any suggestions?
Thanks.

---

### Post by oxsyn on 2008-05-24
The card is a Hawking HWUG1 USB wireless adapter with an RALink chipset.  I read in another thread that these devices should be recognized out of the box.  Definitely not happening in my case.

---

### Post by Marat Galiev on 2008-05-25
Hmmm...Do you know about ndiswrapper?
This packages can use you windows *.inf drivers.
Install ndiswrapper,and 
ndiswrapper -i /path/to/you/windows/inf_file
ndiswrapper -mi
ndiswrapper -ma
Works nice for me,with my D-Link wireless adapter.
And then reconnect you adapter.

---

