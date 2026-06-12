---
title: "Performance anomaly when running an application multiple times"
date: 2008-11-23
forum: General Help
---

### Post by mint.chen on 2008-11-23
Dear all,

    This is mint from Taiwan. I'm running an application that is supposed to terminate for around 26.3 seconds. However, when I run it for several times, I find that the execution time of the application will be much slower sometimes.

e.g., the execution time of 20 runs is listed below:
0       26.3261630535
1       26.3124232292
**2       38.3678188324 **     
3       26.2164769173
**4       39.1607196331**
5       26.321944952
6       26.243771553
**7       39.1555733681**
**8       39.1046867371**
9       26.2520837784
**10      39.3060615063**
11      26.2277290821
**12      39.3556072712**
13      26.2933149338
**14      39.162343502**
15      26.2292428017
16      26.3370480537
17      28.6941120625
18      26.2942950726
19      26.3473296165
20      26.2511348724

I have turned off the desktop environment so the experiment is done in text mode. And there are no other CPU intensive processes running.

Configuration of my machine:
Ubuntu 8.04
linux kernel 2.6.16
Intel Q6600 4-core CPU
2GB RAM

I wonder if this is caused by OS scheduling or other OS-depend issue.
Could someone kindly guide me to walkaround this issue??

Thanks,
Mint.

---

