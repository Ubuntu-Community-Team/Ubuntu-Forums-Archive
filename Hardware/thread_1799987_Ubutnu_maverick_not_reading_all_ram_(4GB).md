---
title: "Ubutnu maverick not reading all ram? (4GB)"
date: 2011-07-08
forum: Hardware
---

### Post by michaelg9 on 2011-07-08
Hello,

I have to say that I'm new in Ubutnu, but not so new in Linux.
I've downloaded Ubuntu 32-bit maverick, into my Toshiba Satellite L-300 laptop. I have Linux 2.6.35-30 kernel with KDE 4.5.5
The problem is that this laptop has 4 GB ram, but Ubuntu only reads 2.83 GB, I'm not sure why.
Memtest detects all ram capacity, and it doesn't find any problems, but when I boot into Ubuntu, it only reads 2.83 GB.
I also dual boot with Win7 and it can read all 4GB ram too

Any solutions please?

Thank you

---

### Post by ankspo71 on 2011-07-08
Hi,
If you installed Ubuntu without an internet connection at the time of installation, then Ubuntu wouldn't have been able to automatically download and install the special PAE kernel to allow 32 bit systems to use 3gb or more of ram. See this link on how to check if your system supports using PAE and to see how to install the PAE kernel. [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)
Hope this helps.

---

### Post by michaelg9 on 2011-07-08
Hello

That was it thank you:D
Didn't know that 32-bit systems could use more than 4 gb ram...

---

### Post by foutes on 2011-07-08
> **ankspo71 said:**
> Hi,
If you installed Ubuntu without an internet connection at the time of installation, then Ubuntu wouldn't have been able to automatically download and install the special PAE kernel to allow 32 bit systems to use 3gb or more of ram. See this link on how to check if your system supports using PAE and to see how to install the PAE kernel. [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)
Hope this helps.

Not trying to hijack this thread but thank you I did not know about that kernel.

---

