---
title: "Problems with a Toshiba Satellite"
date: 2005-10-09
forum: Hardware &amp; Laptops
---

### Post by Strangerdave on 2005-10-09
I have a Toshiba Satellite A70 with a P4 2.8 processor, an ATI 9000 graphics card with 64 MB of ram.  I have tried both the new Breezy 5.10 live CD and the Hoary 5.04 live CD, but neither of them have worked.  I boot from the CD, and get to the screen where I am to select "enter" and I see packages unloading, but then my Laptop just stops working.  Is there something I should do in the BIOS maybe?

-SD-

---

### Post by matthew on 2005-10-09
Laptops can be tricky. For mine, it only worked if I booted using the command vga=771. like this:

linux vga=771

or

live vga=771

You could try that. There are other options as well. When you first boot from the cd you can hit F1, F2 and so on and it gives some idea to try if you have trouble.

---

### Post by Elv13 on 2005-11-13
disable lcd scratch in the bios, and usb legacy too

---

