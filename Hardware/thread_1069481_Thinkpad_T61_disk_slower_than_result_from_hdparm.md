---
title: "Thinkpad T61 disk slower than result from hdparm"
date: 2009-02-14
forum: Hardware
---

### Post by zhanginseattle on 2009-02-14
Hi, all

I bought a Thinkpad T61 in last October. I erased Vista and installed Ubuntu 8.7 and later upgraded to 8.10. The disk speed seemed slow. I tried the following command to test the real read speed:

      $ date; cp a_100_MB_file /dev/null; date;

The copying takes about 20 seconds. So the speed is about 5MB/sec.

But when I try to use hdparm to test the read speed, the result is like this:

   $ sudo hdparm -t /dev/sda

   /dev/sda:
   Timing buffered disk reads:  130 MB in  3.03 seconds =  42.84 MB/sec

Can anybody tell me why the real read speed is far from the 42.84MB/sec?

Thanks,
ZhangInSeattle

---

