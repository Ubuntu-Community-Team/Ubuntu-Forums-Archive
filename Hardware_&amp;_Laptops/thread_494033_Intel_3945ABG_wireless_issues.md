---
title: "Intel 3945ABG wireless issues"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by JamesCurtis on 2007-07-06
Hey guys, I got the notice of the restricted module, so I went about downloading the intel driver and trying that out.  The driver I ended up going to was the newest driver at the sourceforge open 3945 driver website (which intel pointed me to).  I messed around and finally got online, but now I have another problem.  Before when I was using the restricted module it would let me do the swscanner and other programs, I just couldn't get online.  
I installed the following packages to get it working without the restricted driver

ieee80211-1.2.17
ipw3945d-1.7.22
ipw3945-ucode-1.14.2
ipw3945-1.2.1

I can connect to the access point just fine, bu t when I try to sniff the interface it doesn't list the interface as sniffable, and when I try to use swscanner with it, it crashes when i start the scan.  

The description swscanner gives me is it crashed and caused the signal 11 (SIGSEGV).

Thanks for the help :)

---

### Post by miika on 2007-07-06
Did you compile the driver with monitor mode enabled? If not, edit Makefile and set
```
CONFIG_IPW3945_MONITOR=y
```

---

