---
title: "New server using i7 6700 skylake cpu and ubuntu 14.04.3 compatibility"
date: 2015-11-14
forum: Hardware
---

### Post by hotsummer55 on 2015-11-14
I want to use a i7 6700 skylake cpu for a server as it support 64GM of ram .I know this is not a server cpu but budget is tight
[http://ark.intel.com/products/88196/Intel-Core-i7-6700-Processor-8M-Cache-up-to-4_00-GHz](http://ark.intel.com/products/88196/Intel-Core-i7-6700-Processor-8M-Cache-up-to-4_00-GHz)
and probably this board
[https://www.asus.com/uk/Motherboards/Z170-PRO-GAMING/specifications/](https://www.asus.com/uk/Motherboards/Z170-PRO-GAMING/specifications/)

My question 
From what iv'e researched skylake will be supported in the 4.3 kernel but ubunu 14.04.3 is on at most 3.19
If i use a 3.19 kernel with this cpu will system still work or will i have stability problems
I guess the new feature of cpu won't be supported but at the moment my main concern is stability .
I suspect when we get to 16.04 the lts enablement stack will back port that kernel but i want to setup before then

---

### Post by mörgæs on 2015-11-15
According to this
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1)
an i7 seems to run best with 15.10.'

---

### Post by hotsummer55 on 2015-11-15
I think 15.10 is on 4.2 kernel and this i think will be available to 14.04 on lts enablement stack in a while feb 2016 .
I suppose if phoronix are testing on older kernels then its stable.I won't be using graphics no X on server and i did see they used a mod on kernel to work.
Skylake needs this boot parameter: i915.preliminary_hw_support=1

---

