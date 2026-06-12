---
title: "Can't connect to Epson Perfection V500 Photo scanner"
date: 2014-10-04
forum: Hardware
---

### Post by lift_test on 2014-10-04
I have installed Sane-PYGTK and gscan2pdf but both report "no scanner reported by sane" or "no device found". In the help for gscan2pdf I found this suggested command "gscan2pdf --device <device>", I tried that but couldn't find the correct incantation to replace <device>, any suggestions please?

---

### Post by lift_test on 2014-10-04
I've tried downloading the drivers from the epson site but when I try to open in software centre it says "Dependency is not satisfiable:iscan(>=2.16.1).  Does this mean I'm trying to use a too recent driver?

---

### Post by Enigma12 on 2014-10-04
May not work for you, but I just installed an Epson 1200U scanner to my Lubuntu 14.04 32-bit computer yesterday, and it is working fine. Here's what I did. First, I installed iscan_2.29.3-1~usb0.1.ltdl7_i386.deb, then did the same with iscan-data_1.29.0-2_all.deb, both which I downloaded some time ago. I think I got both files from the Epson website. 

I think the first one gave me a similar or identical dependency notice, but the second seems to have solved that. When I tested the scanner, using Image Scan! for Linux, which I got from the Lubuntu Software Center, I got very good scans. Some of the menus in Image Scan were greyed out, but I was able to get perfectly acceptable scans anyway. 

Perhaps those two files will solve your problem also.

---

### Post by sammiev on 2014-10-04
You need both files for your scanner to work.

---

