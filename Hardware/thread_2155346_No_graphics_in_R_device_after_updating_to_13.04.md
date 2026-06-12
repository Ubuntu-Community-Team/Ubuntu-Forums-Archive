---
title: "No graphics in R device after updating to 13.04"
date: 2013-06-18
forum: Hardware
---

### Post by hanansela on 2013-06-18
Hello
I have recently did a clean install of Ubuntu 13.04 on my machine (Lenovo Think-pad Edge, 64bit, Intel® Ironlake Mobile graphic, Intel® Core™ i5 CPU M 480 @ 2.67GHz × 4). The R graphic device opens but does not show any graphs. I got a hint in R forums that it might have some thing to do with graphic drives. I can not see additional drivers available to my machine and I wonder whether it is advisable to try and look for different drivers and where to look for them? The driver I have now is: Intel® Ironlake Mobile.
Thank you

---

### Post by Yellow Pasque on 2013-06-18
> The R graphic device opens but does not show any graphs. 
What is an R graphics device?

> I can not see additional drivers available to my machine
Intel video drivers are open-source and are included in the kernel. They do not show up in this dialog and you already have the best video drivers.

---

### Post by hanansela on 2013-06-18
R device is a window that opens to show graphs when you use R statistical language in it's console.

---

