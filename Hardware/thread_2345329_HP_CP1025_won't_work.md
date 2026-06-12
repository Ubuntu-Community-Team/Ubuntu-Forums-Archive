---
title: "HP CP1025 won't work"
date: 2016-12-03
forum: Hardware
---

### Post by pedro_rodriguez2 on 2016-12-03
Hi, 

I just bought an HP CP1025. This is not a very new model, so it should work ok. I have the latest version of hplip installed. It is recognized, but nothing happens when I say 'print test page'. Not even an attempt at printing. It did print its own self test configuration when I first switched it on, so I know it can print.

I added it in System Settings> Printers. It is connected and switched on. I also made it the default printer.

I can't think of what more I can do? Any tips please?

I tried it in 14.04 and 16.04, but it does not print.

Solved: even though it is seen, you need to run hp-setup -i That threw up a lot of errors and problems, but the printer now prints!!

---

