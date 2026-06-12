---
title: "Black frame on Compaq Armada 3500"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by Gro70 on 2007-09-05
Hi,

I´m a Linux-novice and have just installed Ubuntu 6.10 on a Compaq Armada 3500 (an 8 year old Laptop) but I´m still unable to change the resolution to more than 800*600. Ubuntu boots with a black frame.

Hardware: The graphicschip is a "Chips F96000" (the Ubuntu-devicemanager works correct here), the maximum possible (and desired) resolution of the TFT is 1024*768.

Some posts recommend to run reconfiguration of xserver ("sudo dpkg...-xorg") but on my machine this doesn´t have any effect at all, although I´ve marked "1024*768". The highest possible setting in "Displaysettings" remains after reboot on 800*600.

In another forum somebody says (its unfortunatly an older post) that there have to be some changes in Grubs "menu.lst" by adding "vga=791" in the "kernel"-line. But I´m completly unfamiliar in making such detailed changes in Linux/Ubuntu and so I don´t  know how to find and how to manage and if this is right at all. 

Can anybody help me? Please remember: I´m quite fresh (worked on Win98SE for a long time...) and need some more detailed advice.

Thanx for help!

---

