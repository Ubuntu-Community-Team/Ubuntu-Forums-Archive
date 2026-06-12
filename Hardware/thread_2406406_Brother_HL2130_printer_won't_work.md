---
title: "Brother HL2130 printer won't work"
date: 2018-11-20
forum: Hardware
---

### Post by imgeka on 2018-11-20
Hello,

I installed the driver for the mentioned printer, but as it was going to perform its first test print, the command terminal merely showed [............] supposedly to indicate work in progress, but nothing happened.

Later I checked the OS to see if the Printer was installed, and it it did indeed show the HL2130 as installed. Even so, it does not print.

Could someone please help me out with this issue?

---

### Post by imgeka on 2018-11-21
This is urgent; can anyone help?

---

### Post by imgeka on 2018-11-21
Is it perhaps possible to install the printer-finding software of Ubuntu 18.04 on Xubuntu 16.04 Xenial Xerus? In Ubuntu 18.04 the printer is semi-automatically recognised.

---

### Post by slickymaster on 2018-11-21
*Thread moved to **Hardware**.*

---

### Post by SeijiSensei on 2018-11-21
Go to the Brother support site and download the "Driver Install Tool," then run it from the command prompt using sudo.

[https://support.brother.com/g/b/downloadlist.aspx?c=us_ot&lang=en&prod=hl2130_all&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us_ot&lang=en&prod=hl2130_all&os=128)

---

### Post by kurt18947 on 2018-11-21
> **imgeka said:**
> Hello,

I installed the driver for the mentioned printer, but as it was going to perform its first test print, the command terminal merely showed [............] supposedly to indicate work in progress, but nothing happened.

Later I checked the OS to see if the Printer was installed, and it it did indeed show the HL2130 as installed. Even so, it does not print.

Could someone please help me out with this issue?

What 'flavor' of Ubuntu are you running? Do you have the package system-config-printer? You can tell by pressing 'alt' + 'f2' or opening a terminal then typing the name. If not it can be installed from the repositories. I find that app more useful than the gnome version 'printers'. I use the Brother installer that SeijiSensei mentions and have had good luck with it.

---

### Post by imgeka on 2018-11-21
Thanks for your reply. I just upgraded to 18.04 and the printer was recognised within a matter of seconds.

---

