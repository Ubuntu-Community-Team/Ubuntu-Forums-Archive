---
title: "Printer Help?"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by fuxxtor on 2007-05-03
I have a Brother 2070n printer, and am having a heck of a time with it.  Perhaps someone here can help me out?
I've installed and configured the printer according to [this tutorial]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser") .

I've also tried setting the printer up as an LPD printer, but in both cases, the printer will print one page with some garbage on it (it looks kinda like a header of some sort, with information about the print job), and then will print blank pages endlessly; or at least until I cancel the print job, let the printer run out of paper, power it down and then power it back up.

Does anyone have any idea what's going on and how I might fix it?

---

### Post by fuxxtor on 2007-05-04
Solution:

[Brother FAQ]("http://solutions.brother.com/linux/sol/printer/linux/cups_network.html")

And you also need to do:

$ sudo adduser cupsys shadow

$ /etc/init.d/cupsys restart

so you don't get hung up at the CUPS password stage.

In fact, despite having my account as an administrator on the computer, I had to enter the login and password that were input during the 6.10 installation process.

---

### Post by PRMan on 2007-05-22
> **fuxxtor said:**
> I have a Brother 2070n printer, and am having a heck of a time with it.  Perhaps someone here can help me out?
I've installed and configured the printer according to [this tutorial]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser") .


Thanks, I got my 2070N working through Windows using that tutorial.

---

