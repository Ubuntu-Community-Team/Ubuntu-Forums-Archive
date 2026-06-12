---
title: "Memory Upgrade Problem"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by ChuckL on 2007-10-15
I have been running Ubuntu 7.04 on a Dell GX270 with 2.2G of memory without any problems. I just upgraded the total memory to 4GB. Upon rebooting I can log on but then as soon as I attempt run an app the screen goes black and I cannot get it back.

Is there any way to utilize 4GB of physical memory? I have read where there was (is?) a 3GB limit but then I also find references to i86 32-bit machines supporting 4GB etc. 

Chuck

---

### Post by rsambuca on 2007-10-15
I'd run the memtest overnight before doing anything else.

---

### Post by ChuckL on 2007-10-16
Thanks for the suggestion. I ran the memory test and it never found any errors; however I did discover a few more things that might be pertinent. The bios stated that I had 4096MB of memory but using free -m displayed only 3276MB of total memory. I checked the boot configuration parameters and CONFIG_NOHIGHMEM=No, CONFIG_HIGHMEM64G =Yes, and CONFIG_HIGHMEM=Yes. I modified the GRUB boot parameter with mem=4096m and rebooted but I still saw only 3276MB of total memory. While I could run a terminal session, and a few other utilities, as soon as I tried to run Firefox the system would hang and the screen went black. 

I removed one stick of memory and rebooted using only 3072MB of memory. Things appear to be working. I am suspecting the memory stick but will play around with that later to see. 

Regards,

Chuck

---

