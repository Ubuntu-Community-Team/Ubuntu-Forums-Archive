---
title: "printer minolta 2400 w not working"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by could on 2006-06-30
Hi!

I've tried to install a printer driver for my Minolta 2400w color laser printer.

The printerdriver is a download from:

[http://sourceforge.net/projects/m2300w/](http://sourceforge.net/projects/m2300w/)  (m2300w-0.51.tar.gz)
 
after installing the build-essential I was able to ./configure/make/make install without any obvious errors.

I then tried to setup the printer via System->Administration->Printers (german: Druckvorgang)
choosing the newly available KONICA MINOLTA Folder and the 2400 Printer driver.

It works without throwing errors and I end with a 'ready Printer' which takes jobs.

But these Jobs never print. When I take a look at the properties of the printer I find the printer is displayed as 'not connected' and the driver choosen is  

magicolor2430DL (which i have not choosen) and the connection-typ is displayed as networked (which i also did not choose)

Changing these entries does not seem to change anything as the old entries are displayed after closing and opening of the Printer-Properties.

I would be gratefull for any hints or corrections!

could

---

### Post by taladon on 2006-08-19
Hello.
I am in the same boat you are.
Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=159904&highlight=konica+minolta](http://www.ubuntuforums.org/showthread.php?t=159904&highlight=konica+minolta)
I've had some success with my Konica Minolta 2400w by manually compiling the latest version of cups (1.3x series) and then compiling the m2300w driver.

--Taladon

---

