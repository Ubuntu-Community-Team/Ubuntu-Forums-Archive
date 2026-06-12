---
title: "No nvidia driver after kernel update"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by AlFrugal on 2009-02-02
I'm running Ubuntu 8.10. This past week there was a kernel update to 2.6.27-11. Following this update, whenever I boot kernel 2.6.27-11 I get a boot message "DKMS auto installation service for nvidia kernel module 173.14.12 FAIL". Ubuntu then boots into "low graphic mode".

Prior to this update, I had been using nvidia kernel module 173.14.12. It was installed via envyng.

I've read that DKMS can fail if kernel headers aren't installed. I have linux-headers-2.6.27-11 installed.

How can I fix this problem (and what caused it)?

---

### Post by cariboo on 2009-02-02
Have got build-essential installed?

Jim

---

### Post by AlFrugal on 2009-02-03
Thanks very much for your reply! I did not have build-essential installed. I installed it and rebooted. This time DKMS installed the nvidia driver.

---

