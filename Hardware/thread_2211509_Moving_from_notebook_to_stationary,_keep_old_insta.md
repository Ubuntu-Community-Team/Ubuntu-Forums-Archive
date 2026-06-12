---
title: "Moving from notebook to stationary, keep old install?"
date: 2014-03-16
forum: Hardware
---

### Post by kd6C7fP on 2014-03-16
I've decided to move from my Clevo W110ER Notebook, to a custom built work-station. I'm keeping the SSD from the notebook for OS use in the new computer. If possible, I'd like to keep my old install (Ubuntu 13.10 X64), to save me the hassle of backups and reinstalls.... Is this possible, and if so, worth the hassle?

Old notebook:

Clevo W110ER
I7 3610QM CPU
Geforce 650M GPU 


New PC:
I5 4670K CPU
R9 Radeon 270X

Any help appreciated. :)

---

### Post by sudodus on 2014-03-16
If you have proprietary drivers, you need to reconsider them. Otherwise Ubuntu is portable.

In your case, I suggest that you remove the nvidia proprietary driver (as I guess you have) and let the computer use the free driver (it should find a driver for the radeon card in the new computer).

Depending on wifi chip/card, you may also need to remove a proprietary driver for wifi.

Later on you can check if there are some proprietory drivers that are suitable for the new computer, and install them.

---

