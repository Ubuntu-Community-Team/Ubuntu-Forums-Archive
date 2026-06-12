---
title: "VERY ugly RAM problem"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by Denn1s on 2007-08-02
I have been having a lot of trouble extracting RAR archives in my desktop, always corrupted, no mather wath OS, nor wath hard drive, no mather how many times i downloaded, no mater wath i downloaded. 

so i finaly thought it may be the RAM, so i ran memtest in grub.

i started it a little over an hour ago, its currently in pass 2, and so far it has fount 1170 errors, and no i didnt missespelled, it says one thousand one hundred seventy five errors (it increased while writing this)
so, is this too bad? has the RAM been rendered useless?, its only a 256 DDR but they are expensive and hard to find for me at least. is there a way to correct this? how long am i suposed to run memtest? 


Ps. i cant answer today the posts so ill answer till tomorrow morning, tanks for ur help

Pss. the test got to pass 3, finding 1400 errors, and rising rapidly, ill stop it since i must leave, thanks again

---

### Post by OoooMatron on 2007-08-02
It could be one of two problems. 

1. The ram is knackered so you will need to buy new

2. You have a motherboard that is running in too fast a mode for the ram to handle. Sometimes the bus speed can upset the ram.

I had this problem once about 5 years ago with a motherboard that was supposed to run my 266 DDR ram but didn't. I had the same problem you described above and on a hunch I reduced the bus speed to 133 in the bios and lo and behold the ram had zero errors when running memtest.

Try reducing the bus speed. Your cpu will be severely underclocked but it will let you know if the RAM is ok or not.

---

