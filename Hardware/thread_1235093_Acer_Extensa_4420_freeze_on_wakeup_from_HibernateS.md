---
title: "Acer Extensa 4420 freeze on wakeup from Hibernate/Suspend"
date: 2009-08-08
forum: Hardware
---

### Post by pbidwell on 2009-08-08
Ubuntu 8.10 runs beautifully on my 4420, except for a lock-up whenever the laptop goes into hibernation or suspend :(.  I can wake the laptop up, but when the desktop reappears, it is completely frozen.  I ran a few Google searches and came across the Laptop Testing Team page on my Acer model [here]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerExtensa4420").  They confirm my problem:  The Acer freezes after suspend or hibernation.  Are there any Ubuntu geniuses out there with some miraculous workarounds?  Does anyone know of any threads that could be helpful?  I am very new to Ubuntu and any help is appreciated.

Thanks.

---

### Post by dlstyley on 2009-10-10
I believe this has to do with the fglrx driver.  If you use radeon instead, then it will suspend and resume properly.  Note however that you won't get any of the supposed performance benefits from the fglrx driver.

---

