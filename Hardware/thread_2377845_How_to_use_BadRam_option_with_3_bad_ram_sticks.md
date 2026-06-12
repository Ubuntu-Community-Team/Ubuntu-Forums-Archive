---
title: "How to use BadRam option with 3 bad ram sticks"
date: 2017-11-17
forum: Hardware
---

### Post by xcom3 on 2017-11-17
Hello all!

I have 4 PCs DDR3 1333Mhz Ram stick, and 3 of them are faulty. 
If I can record the bad addresses with memtest86+, is it possible with ubuntu 17.10 to exclude the problematic parts?
BadRam module is complied into the stock kernel?

I have bad addresses at :
Address: 25EDDF830, Expected: 00000080, Actual: 80000080
25F5A1768, Expected: 00200000, Actual: 00000000
A23C2440, Expected: CD969AD2, Actual: CD969ADA

Is it good this way?

GRUB_BADRAM="0xA23C2440,0x25EDDF830,0x25F5A1768"

---

### Post by Autodave on 2017-11-17
$32 at Newegg for a 4 gig.  If you have 3 that are bad, I think it is time to quit fooling around with them. If they are all one gig, you would be better off running from the one good one and leaving the other 3 out of the machine until you can get some more RAM.

---

### Post by efflandt on 2017-11-19
Amazon also has 4 GB DDR3 1333 non-ECC RAM in that price range (note that some you might find is ECC RAM for servers). If it is an older PC like mine 4 GB may be max for each slot. I got (4) 4G Samsung DDR3 1333 RAM from Amazon at the same time I ordered an i7 870 to upgrade my i5 650.

---

