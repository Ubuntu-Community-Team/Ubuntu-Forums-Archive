---
title: "Is it possible to install two printers in ubuntu10.04LTS?"
date: 2012-03-03
forum: Hardware
---

### Post by arroy_0209 on 2012-03-03
I have one canon laser printer installed with ubuntu 10.04 and I need to install another deskjet printer which also has a scanner with it. The question is: will the printers work properly if I install both? Is any special step has to be taken? I heard that one printer works fine but two printers installed creates problem.

---

### Post by nd456 on 2012-03-04
I have two printers on one of my Ubuntu's. The tricky part is getting to printers with Ubuntu support.

---

### Post by Ms. Daisy on 2012-03-04
What's the second printer- is it an HP? 

Will they both be installed directly to your machine or will they be network printers?

---

### Post by arroy_0209 on 2012-03-05
Yes, the second one is HP deskjet and both will be installed in my personal computer, not to be used as network printers. So what should I do?

---

### Post by Ms. Daisy on 2012-03-05
I'm not aware of any problems with having two printers attached to one  computer, but that doesn't mean there aren't any.  Maybe there could be  issues if there were two of the same type of printer? 

It's as easy as plugging in the new printer and having Ubuntu  automatically detect it if you only want to print with the new HP  printer.  [https://help.ubuntu.com/10.04/printing/C/printing.html](https://help.ubuntu.com/10.04/printing/C/printing.html)

However, if you want to print & use the scanning function of the HP  printer, then you need to install HPLIP, which is in the Ubuntu Software  Center.  I'm pretty sure it has a wizard-type setup process that was  pretty easy to follow.  (choose either HPLIP or the help.ubuntu.com  method described above- you can't do both)

I recommend that you make sure HPLIP supports your printer first:
 [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

You'll also need to install the driver for the printer. My HP driver  needed to be downloaded from the HP website but yours may be included in  Ubuntu's repositories. If the driver isn't automatically detected  through the printer setup process, then post back.

---

### Post by fjgaude on 2012-03-05
I have an Canon and an Epson; they both work fine. Can't say about multi types, scanners, etc.

---

