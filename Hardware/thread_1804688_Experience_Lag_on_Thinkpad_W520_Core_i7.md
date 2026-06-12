---
title: "Experience Lag on Thinkpad W520 Core i7"
date: 2011-07-15
forum: Hardware
---

### Post by corck on 2011-07-15
Hi,
I have a new Thinkpad W520 Core i7 and experience that there is somehow a lag it seems.
I first realized it, when I am running Cucumber tests that previously took ~20min (and for all other devs take this long) and on my freshly installed Kubuntu 11.04 64bit takes 117 minutes.
In the meantime I realize that the applications sometimes won't react for 1-few seconds when I switch between them.

I looked at iotop and cannot see lots of activity there. I have 12GB of Ram and only ~5Gb used. When I run the test only 1-2 show high activity.

I read something about Sandybridge not beeing well supported on Kernels < 2.6.39 so I upgraded to this one:
Linux thinkpad 2.6.39-02063903-generic #201107091121 SMP Sat Jul 9 11:25:36 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

