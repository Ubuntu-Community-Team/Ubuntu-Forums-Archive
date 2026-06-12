---
title: "HD's wrongly recognised as SATA"
date: 2009-06-17
forum: Hardware
---

### Post by Cheule on 2009-06-17
Hi folks,

I'm running Ubuntu 9.04, the OS is mounted on sda while video files are going to be used on the second drive, sdb.

The only trouble is, since I tried doing some file transfers, I noticed that I was only getting 2.7MB/s, which is terrible compared to 6.06LTS. This led me to these forums to read up on terrible SATA performance in the last two Ubuntu releases.

All well and good, except both my drives are PATA. In fact, the motherboard predates SATA so I'm not sure why Jaunty thinks my drives are SATA!

I was just wondering if I could somehow change some config file somewhere to correct this, or is this a 9.04 bug?

For futher info, sda is a 120gb 7200rpm Maxtor Diamondmax+9, and sdb is a Samsung 160gb 5400rpm type. Transferring a file between both drives is slowest of all, only 2.7-3.8MB/s, while transferring a file from either drive to a networked Windows machine results in a slightly better 7.2MB/s.

What can I do to remedy this?

Any help appreciated. :)

---

