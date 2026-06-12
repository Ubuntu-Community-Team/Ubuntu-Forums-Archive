---
title: "Loading cpufreq kernel modules failed"
date: 2013-08-16
forum: Hardware
---

### Post by suomalainen on 2013-08-16
HI !

I just finished installing MATE into 12.04 and during the install process via terminal I noticed the following Failure:

Loading cpufreq kernel modules failed

next to it in red letters was the word "fail"

I attached a screenshot of the error msg.

How should I proceed with this failure?

Thank you very much.

---

### Post by tgalati4 on 2013-08-16
No worries.  The kernel tries to insert a module that allows for frequency scaling, say 800MHz to 2400MHz (2.4 GHz) in steps.  Some laptops with Intel processors have this feature.  Yours does not.  It should work just fine.

If you want to remove this error in the future, then research *blacklist cpufreq*.

---

### Post by suomalainen on 2013-08-16
Thank you very much for the feedback and the FYI on removing the error.!

---

