---
title: "Intel SSD read/write speeds slowed to 700 KB/s"
date: 2011-10-09
forum: Hardware
---

### Post by runesvend on 2011-10-09
Hi

I have been using my 80GB Intel X25-M SSD for a little over two years now. And until now, with great performance.

Since a couple of days ago I noticed that my system had slowed down considerably, so I ran some benchmark tests with iozone to check the read speeds of the system disk, which is the SSD:


```
                                                            random  random
              KB  reclen   write rewrite    read    reread    read   write
            8192       4     725     679      615      679     474     611
            8192      64    9688    7083     7320     5474    5419    5738
            8192     512   64932   63909    93244    78712   66976   45500
```

512KB reads/writes look fine, but 4KB reads/writes have dropped  to 400-700 KB/s.

I presume this is what makes apt-get so slow, it takes ages to install anything (compared to how fast it went before).

I've tried using the wiper script found in the hdparm to do online wipes (ie., with the system running from the disk in question) and this hasn't helped.

Have anyone else experienced anything similar? And what have you done to solve it?

---

