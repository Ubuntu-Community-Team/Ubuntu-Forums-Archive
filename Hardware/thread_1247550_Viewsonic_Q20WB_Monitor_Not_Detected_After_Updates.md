---
title: "Viewsonic Q20WB Monitor Not Detected After Updates"
date: 2009-08-23
forum: Hardware
---

### Post by Matrix_NEU on 2009-08-23
So let me summarise my situation (please go easy on me, i'm pretty new to linux):

In Ubuntu 8.04, I was never able to correctly configure my monitor (Viewsonic Optiquest Q20WB).  The monitor would not detect correctly, and it would default to a set of incorrect resolutions (my monitor is native 1680x1050).  Eventually, I was able to create a custom xorg.conf file which would give me the correct resolutions, but I had other issues, such as the monitor not going to sleep when there was no input ( I would just get a black screen, but the monitor would still be on).  

When I upgraded to 9.04, I was happy to discover that with the NVIDIA driver, my monitor was correctly detected and I could pick the correct resolution without any fuss, plus everything "just worked".  However, I recently installed recommended updates, rebooted my computer, and now I have discovered that the situation is back to the way it was before (the monitor is just listed as "crt-1" in the Nvidia X Server Settings Utility)

I am using the NVIDA propietary driver version 180
Geforce 8800GTS 320 MB

Here are my questions:
1. Is there a way to roll back the updates that were installed over the last few days and see if this corrects the problem.  (why does installing updates break my system...?)
2. Is this issue related to my monitor, GPU, or drivers?
3. Is there another way of permanently correcting this other than my previous hacked solution of editing the xorg.conf file?

Please let me know if you need any other information to analyze this problem. I'm not sure what information is relevent/useful.

---

### Post by Matrix_NEU on 2009-08-24
No ideas on this? Am I not providing some information that is necessary to figure out what is going on here?

---

