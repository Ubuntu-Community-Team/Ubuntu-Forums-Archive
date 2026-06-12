---
title: "Max Ram"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by Chadwick17 on 2007-09-18
I'm looking to purchase a new computer and just wondering what the max supported RAM is for Ubuntu/Linux? I've heard that some macs support 16GB out of the box...

---

### Post by ryanVickers on 2007-09-18
with a 32 bit version of any OS, the max is 4GB, but then in the 64 bit world, there's really no humanly comprehensible limit, so that would leave you with the limits of your motherboard, and, yes, Ubuntu.  I think there's no reason that is shouldn't be able to handle at least 8Gb! :)

---

### Post by w4ett on 2007-09-18
Agreed.  

Here is a good discussion regarding Usable Ram and Swap in 32 and 64 Bit systems:

[http://ubuntuforums.org/archive/index.php/t-472664.html](http://ubuntuforums.org/archive/index.php/t-472664.html)

---

### Post by Chadwick17 on 2007-09-19
Thanks for the link - thats pretty useful. It looks like the sky is the limit under 64bit - I would like to see the application that would utilize all of that RAM.

So, knowing that, I have a more specific question to my setup. I have 2GB RAM and I set up a swap of 1GB when I partitioned. If I were to set up the swap partition at 2GB would I see much improvement in day to day use? (I'm thinking while I run XP in a VM). And if that is the case, is there a way to modify my swap partition without having to reinstall everything?

Thanks again

---

### Post by ryanVickers on 2007-09-19
If you can shrink your partition from the right (assuming the swap's at the end) then you should be able to create a new swap - no data is lost.  You would have to boot from the live CD however.

Personally, 2Gb is enough and 1Gb of swap is fine.  increasing RAM or SWAP doesn't increase performance.  Swap is just in case you run out of ram, and is very slow in comparison.  people just add more ram to "improve performance" because they're running out of ram all the time ind it's using swap/windows pagefile.  If you have never used up all of your 2Gb, you don't need more of either. :)

---

### Post by Chadwick17 on 2007-09-19
The only reason I would be concerned with it is so I can allot more RAM to the XP virtual machine I would be running. But it sounds like memory from the swap wouldn't be too useful anyway...

---

### Post by w4ett on 2007-09-19
I'd have to agree with ryanVickers on that one.  Personally I use 2 Gb on a 32 bit with 1 Gb swap and have yet to dip into swap....but considering the price of ran these days though, 4Gb ram won't be overkill on 64 Bit IMO (2GB will do it for you though).....leaves you with plenty of headroom for a modest outlay of $$$ and plenty of ram for VM.

---

### Post by Chadwick17 on 2007-09-19
Sweet. I'll leave it set up as is then. Thanks for all the advice. I appreciate it.

---

### Post by CREEPING DEATH on 2007-09-19
> **w4ett said:**
> Agreed.  

Here is a good discussion regarding Usable Ram and Swap in 32 and 64 Bit systems:

[http://ubuntuforums.org/archive/index.php/t-472664.html](http://ubuntuforums.org/archive/index.php/t-472664.html)

Except that discussion is wrong, it states that RAM+Swap must be less than 4GB and that is wrong.  **32-bit Linux can't address more than 4GB of RAM, swap does not factor in to it.**  Debian has a BIGMEM kernel that can address >4GB in 32-bit.

CD

---

