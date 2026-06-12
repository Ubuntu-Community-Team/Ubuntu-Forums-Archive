---
title: "PRINTER: Lexmark Z55 worked in 9.04, doesn't work in 9.10"
date: 2009-11-30
forum: Hardware
---

### Post by isntthatamusing on 2009-11-30
When I had Ubuntu 9.04 installed, I installed the Lexmark Z55 drivers for CUPS and my Dell A940 printer worked fine. It was able to print in grayscale just fine. When I upgraded to karmic koala 9.10, and went through exactly the same install process that I used in 9.04, the printer no longer worked. It will not print a test page or a regular page. I tried to use the troubleshooter but that didn't work. I think there is a regression in how CUPS supported/accessed my printer before, and I'd like to know what to do now to make it work. I figure I either have to a) roll back to a previous CUPS driver or b) ??? don't know. Literally everything is set up exactly the same as it was before. Thanks for your prompt help, as I have to print something soon today.

---

### Post by isntthatamusing on 2009-11-30
SOLUTION FOUND:

I checked the CUPS error logs, and the problem was libstdc++5 was missing. This was not available in the karmic repositories, so I had to use the one from jaunty. I installed the .deb for libstdc++5 from Jaunty and the printer worked. Don't know if this was the best solution, but hey, its printing, so I don't care.

---

### Post by isntthatamusing on 2009-12-01
[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

---

### Post by KiDQUiCK on 2010-01-17
Thanks for your suggestion. I had the same problem with my U9.10 networked HP printer when trying to print from a Vista64 laptop -- Win error code was 0x0000000d. After installing libstdc++5 the problem persisted with same error message. My solution was to manually map a printer to LPT1 on Vista -- more here: [http://ubuntuforums.org/showthread.php?t=1313049&page=4]("http://ubuntuforums.org/showthread.php?t=1313049&page=4")

---

