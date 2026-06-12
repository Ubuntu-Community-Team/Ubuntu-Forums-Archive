---
title: "TRIM (for SSD drives), cloning your boot partition and other esoteric anxieties..."
date: 2011-01-29
forum: Hardware
---

### Post by allbread on 2011-01-29
So I had an SSD drive fail on me but after some amount of nagging I've managed to get Crucial (I was attempting to install Ubuntu 10.10 on a CT256M225 256GB SSD drive) to agree to an RMA which will likely take around 10 days all told.

In the interim I have a older 250GB 7200.1 drive that I'd like to install Ubuntu on - my plan is to clone the boot partition over to the replacement SSD when I get it back.

My concern: will the OS still be configured for TRIM if it was installed on regular (platter) drive and then cloned over to an SSD? 

I know TRIM is kernel specific (I believe in 2.6.35) but I'm not sure how or if it needs to be turned "on" or "off".

Is there a way to verify that Ubuntu is actually TRIM'ing the writes on a given drive...?

Also, can anyone out there suggest a good tool for cloning a drive in Ubuntu? 

I've found a couple procedures online for doing this but as prone to  breaking things as I am any kind of helper utility would probably do me  some good...

---

