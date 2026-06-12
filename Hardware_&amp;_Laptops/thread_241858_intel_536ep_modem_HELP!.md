---
title: "intel 536ep modem HELP!"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by chopin1998@gmail.com on 2006-08-22
Hello everybody!
 
 I have a modem using 536ep chip by Intel.
 
 I'm using ubuntu 6.06 and kernel 2.6.15.7 compiled by myself.
 
 I download the driver from [www.intel.com](www.intel.com) ,using gcc-3.4. Compile and load modules is successful.
 And I can use minicom run lots of AT-command-sets,
 
 The question is when I dial-out(ATDT),it show me No DialTone.....
 
 I hope some one nice can help me ! Thank you !

---

### Post by zxee on 2006-08-23
I'm not familar with that modem, but have spent or wasted a lot of time fooling with dial up. (depends on ones perspective; wasted vs spent) Congrats on giving minicom a go it does teach you things about how your modem communicates.
I'm going to assume you have your modem driver working, but if you begins to have doubts on that the best site to look for info on is [www.linmodems.org](www.linmodems.org) 
So try to configure your dial up and modem with this command from a terminal: > sudo pppconfig
That should let you select your modem BTW is the modem internal (PCI) or external? externals are usually /dev/ttyS0 or S1 internals can be from S3 to S6 depending on which pci slot it occupies. Let the thread know how you make out.

---

### Post by chopin1998@gmail.com on 2006-08-23
Thank you for replying.

I know pppconfig, but still NO Dialtone..

Thank you all the same !

---

