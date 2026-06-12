---
title: "HP SMART ARRAY P410 and Ubuntu desktop/server"
date: 2015-03-09
forum: Hardware
---

### Post by darren18 on 2015-03-09
I am wondering what kind of support is out there for using a hp smart array P410 with 512MB write bache and BBU with Ubuntu either 12 LTS or the newest 14 LTS. I would be doing 3 hardware RAID 10's and would obviously need the drives to display in Ubuntu.

Or is there another recommended raid card to use? I am also open to using software raid, but liked the idea of having a cache.

---

### Post by joker535 on 2015-03-10
Looks like it would work fine - [http://manpages.ubuntu.com/manpages/precise/man4/hpsa.4.html](http://manpages.ubuntu.com/manpages/precise/man4/hpsa.4.html)

Not sure on performance. I actually use the P400 with an array of Intel SSDs and it is fine for a workstation with light virtualization.

---

