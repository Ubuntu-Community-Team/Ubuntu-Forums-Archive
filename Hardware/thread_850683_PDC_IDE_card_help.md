---
title: "PDC IDE card help"
date: 2008-07-05
forum: Hardware
---

### Post by neuman1812 on 2008-07-05
Hey all.  I have an old IDE card that i would like to try and use.  My current setup has both my on-board IDE channels used  2 HD and 2 CDROMS

I have a couple of old 20-30gig HD's that I want to add and turn into extra storage.
The output of lspci shows that it does recognize it.


```
root@UB1:/home/walter# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Mass storage controller: Promise Technology, Inc. PDC20267 (FastTrak100/Ultra100) (rev 02)

```

Promise technology.   But when I start the partition editor..it does not recognize the attached drives...  Anyone have an Idea?

Running Ubuntu 7.10
2.6.22-15 -generic

---

