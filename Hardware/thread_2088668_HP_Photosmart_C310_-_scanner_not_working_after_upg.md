---
title: "HP Photosmart C310 - scanner not working after upgrade"
date: 2012-11-27
forum: Hardware
---

### Post by noteviljoe on 2012-11-27
I have a HP Photosmart C310 network printer and scanner.

I had been using both the scanner and the printer successfully over wifi network using my laptop with Ubuntu 12.04 (64) after installing HPLIP toolbox through the software centre.

However, after an upgrade to 12.10 (64) I now get the following error when trying to scan using xsane: 
[INDENT]Failed to open device 'hpaio:/net/photosmart_Prem_C310_series?zc=HPCEB!CD':Error during device I/O[/INDENT]

Printing still works fine.

Help appreciated, I have googled and can't find a solution. I have seen that the HPLIB in the software centre is not the most up to date but it looks like I'd have to manual build the most up to date version which sounds a bit scary.

---

### Post by iainmellis on 2012-11-29
I'm having the same problem:(

---

### Post by iainmellis on 2012-11-29
I've upgraded to hplip 3.12.11 and it now works

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by noteviljoe on 2012-12-04
yeay fixed :)

---

