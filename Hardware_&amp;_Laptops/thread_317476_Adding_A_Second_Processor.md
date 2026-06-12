---
title: "Adding A Second Processor"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by twentytortures on 2006-12-12
I own a dell precision 220, it is a fairly old computer but runs great under kubuntu! Currently it has a single 1000mhz pentium 3. I recently came into possession of a pair of 933mhz pentium 3's. I am not able to use them currently because I need to buy another piece of hardware, a Voltage Regulation Module (VRM), in order to use them. This will cost a little bit of money and I don't want to end up with something I can't use.

My question is: if I get the VRM and put in my two processors, will I be able to continue running kubuntu or will I have to reinstall or reconfigure things? 

Thanks.

---

### Post by insane_alien on 2006-12-12
does the motherboard have sockets for them? i'm thinking no.

---

### Post by twentytortures on 2006-12-12
It has two slot 2's (i believe they are slot 2's anyways).

---

### Post by mbobak on 2006-12-12
Sure, you should be fine.  The default Edgy kernel is SMP aware.

So, just shut down, do the hardware install, power up and and you should see two CPUs if you do a:
cat /proc/cpuinfo

-Mark

---

### Post by twentytortures on 2006-12-12
Okay, cool! Thanks so much for the speedy replys!:D

I now have 2 processors and they work just fine!

---

