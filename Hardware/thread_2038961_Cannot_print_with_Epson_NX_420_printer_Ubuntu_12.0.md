---
title: "Cannot print with Epson NX 420 printer Ubuntu 12.04 desktop"
date: 2012-08-07
forum: Hardware
---

### Post by cal1j on 2012-08-07
Hi,

I am a Linux noobie that is trying to do more without the help of my my Ubuntu mentors. :D I have a Epson Sylus NX 420 printer that has printed fine from my Ubuntu 12.04 desktop before; however, I recently re installed due to some issues I was having. The good news is the re install fixed the problems, but now after a several hour spree on the internet I still can't seem to get the printer to work. I have downloaded and installed the drivers from [http://www.openprinting.org/printer/Epson/Epson-NX420_Series](http://www.openprinting.org/printer/Epson/Epson-NX420_Series) but the printer still wont print. I am using a USB connection from my desktop to my printer. When I look, it lists the printer, but when given a job NOTHING happens :confused: I followed this thread [http://ubuntuforums.org/showthread.php?t=1775653](http://ubuntuforums.org/showthread.php?t=1775653) to install the drivers. I'm lost.

---

### Post by aztecmermaid on 2012-08-16
_**Epson Stylus SX445W (wireless) printer and Ubuntu 12.04:**_

I had trouble for  days trying to get printer to work either wirelessly or via printer  cable. My laptop would see printer but any print job sent to printer  would simply result in nothing at all, or no printing but paper continuously spewed out  of printer!

 Finally found this and ubuntuforums thread mentioned here and followed ramjet_1953's instructions, by installing *Epson NX420 series - DEB for LSB 3.2 *from  openprinting.org (opened it in Ubuntu Software Centre, installed, then  added local/wired printer from scratch) - and it works! :guitar:

Managed to print a test page and a 2 page Libre Office doc.

Thanks you so much! :)   ):P

---

### Post by denomc on 2012-09-20
I had the same issue with my Epson Stylus SX445w, I finally spotted that the location number had changed. Not sure how this happened, anyway print off the settings on you're printer and check the location is correct on the printer setup on the PC. For me the last digit was one less than it should have been.

---

### Post by natespapa09 on 2013-02-09
I installed the driver listed above. My printer prints, and did before intsalling the listed driver above, but it still prints with colors miss aligned. Any ideas? It prints fine from Windows 7.

I figured out what I didn't do. I had to change my printer from Cups to the openprinting.org driver listed earlier. Now it works fine.

---

