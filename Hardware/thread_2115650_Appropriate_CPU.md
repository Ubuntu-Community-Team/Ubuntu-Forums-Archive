---
title: "Appropriate CPU"
date: 2013-02-13
forum: Hardware
---

### Post by ManamiVixen on 2013-02-13
I'm looking to upgrade my computer to a faster CPU and I am unsure as to which CPU would be appropriate for my system. I have a Gigabyte GM41-ES2L Motherboard, Pentium Dual-Core E5500 2.8GHz, 2GB of DDR2 Ram in Dual Channel Mode, Nvidia Quadro 600 Graphics, X-Fi Xtreme Gamer, and 2 320GB sata hard disks running individually, one being my main install drive. My OS is Ubuntu 12.10 64Bit. I use my computer mostly for light multimedia work such as photo editing, music creation, and video editing. My current CPU is ageing and I'm seeing it with slowdowns in rendering videos and such. 

What CPU is best for for this system setup and Ubuntu? I was looking at a Core 2 Duo E7500, but would like a Core 2 Duo E8400. But the 1333MHz FSB of the 8400 scares me due to possible bottleneck with the 800MHz ram and so I feel more comfortable with the 1066MHz of the 7500. Help me decide please?

---

### Post by ahallubuntu on 2013-02-13
~

---

### Post by ManamiVixen on 2013-02-13
Thanks for your input. I decided to get the  E8400. FYI, I would like to upgrade all my core components to new standards like an i5 with 4GB of DDR3 ram, but I am strapped for cash. So for now I will just upgrade the CPU.  I will be building a new system eventually. Also I heard Quad Cores are not worth it since most programs on linux still run using only one or two cores. Would of been a waste. Yes, I am buying from Ebay.  Also I would like to point out that 2GB is enough ram, the real problem lies in swappiness. It is set to high by default. By lowering it's value, like say to 5,  you can defer swap and in turn programs like Gimp and Openshot run better.

---

### Post by ahallubuntu on 2013-02-13
~

---

### Post by Yellow Pasque on 2013-02-13
I hope you didn't pay too much for it. You didn't really gain a lot going from an E5500 to an E8400 (a small clock bump and some cache) since they're both Wolfdale chips (dual-core 45nm). I would have strongly recommended saving that money to use on the next system. I guess you could have also tried to find a cheap S775 quad-core (Q8400).

> Also I heard Quad Cores are not worth it since most programs on linux still run using only one or two cores.
Video editing/rendering is a task that can actually take advantage of more cores...

Sigh.... I hate it when people ask for advice and only give you a few hours to respond before they pull the credit card trigger.

---

