---
title: "hp StorageWorks DAT 24"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by lwf on 2006-07-31
Hello everyone! I have been running Ubuntu 6.06 on my server for a little while now and even if I am still a beginner I dont feel like a actually need to VNC into the GUI any more so I will install the server version instead.

Anyway, I have a hp StorageWorks DAT 24 in this server which I never was able to figure out how to use. Is it even possible to use it with Ubuntu and if it is (that would be really nice actually), how can I do it?

Thanks for your help!

---

### Post by phitoo on 2006-08-04
> **lwf said:**
> 
Anyway, I have a hp StorageWorks DAT 24 in this server which I never was able to figure out how to use. Is it even possible to use it with Ubuntu and if it is (that would be really nice actually),


Use tar. The tape drive is probably /dev/st0 (that's what I have on my servers)

tar czvf /dev/st0 blah blah blah

You may also want the package mt-st to manipulate tapes.

Hope that helps.

---

### Post by lwf on 2006-08-05
Thank you, I am going to try as soon as I get the chance.

---

### Post by davykeenan on 2006-08-16
> **phitoo said:**
> Use tar. The tape drive is probably /dev/st0 (that's what I have on my servers)

tar czvf /dev/st0 blah blah blah

You may also want the package mt-st to manipulate tapes.

Hope that helps.
Hi, can I ask what tape drive you use as I have tried 3 and none of them seem to work, thanks.

---

