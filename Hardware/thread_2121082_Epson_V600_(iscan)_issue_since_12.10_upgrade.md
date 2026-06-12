---
title: "Epson V600 (iscan) issue since 12.10 upgrade"
date: 2013-02-28
forum: Hardware
---

### Post by Numeration on 2013-02-28
I recently upgraded from 12.04 to 12.10 and since then I havent gotten my scanner to work.
The latest iscan-packages are installed and sane seems to find my scanner but despite that the following error messages appears in xsane and iscan.


[IMG]http://i.imgur.com/txOyLtA.png[/IMG]


[IMG]http://i.imgur.com/IhvcYA4.png[/IMG]


```

sane-find-scanner
found USB scanner (vendor=0x04b8 [EPSON], product=0x013a [EPSON Scanner]) at libusb:003:004


scanimage -L
device `epkowa:interpreter:003:007' is a Epson (unknown model) flatbed scanner


dpkg -l | grep iscan
ii  iscan                                2.29.1-5~usb0.1.ltdl7                     i386         simple, easy to use scanner utility for EPSON scanners
ii  iscan-data                           1.22.0-1                                  all          Image Scan! for Linux data files
ii  iscan-plugin-gt-x820                 2.2.0-1                                   i386         Image Scan! plugin for the GT-X820 / Epson Perfection V600 Photo

```

Any suggestions at all would be very helpful!

---

### Post by pdc on 2013-03-02
from the page where you got the iscan drivers;

there is a pdf file [COLOR="#008000"]**userg_revQ_e.pdf**[/COLOR] (the[COLOR="#EE82EE"] _e[/COLOR] means the english version............) 

and it has epson's advice on how to check things

..........one suspects you will need to add epokawa to various config files........

---

### Post by Numeration on 2013-04-03
Did a clean reinstall of 12.10 and now it works perfectly again.

---

