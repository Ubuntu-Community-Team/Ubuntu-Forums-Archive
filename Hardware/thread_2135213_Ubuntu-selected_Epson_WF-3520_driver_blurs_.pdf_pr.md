---
title: "Ubuntu-selected Epson WF-3520 driver blurs .pdf prints"
date: 2013-04-13
forum: Hardware
---

### Post by SaberCat on 2013-04-13
I'm running ubuntu 12.04. When I installed a new Epson WF-3520, ubuntu installed a driver for it. It works fine for most prints -- except .pdf files. They come out blurred! Humm... Any idea what might be causing this. The driver URI for it is: usb://EPSON/WF-3520%20Series?serial=515A47593038353043&interface=1

Thanks in advance...

---

### Post by SaberCat on 2013-04-13
Note: a .pdf file that prints blurred from ubuntu prints fine under Windows 7 on my dual-boot system...

---

### Post by pdc on 2013-04-14
...............I think...........that ubuntu was go to automatically go here...................

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

and download the appropriate Epson driver 

which should be from this list

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71)

If you open up synaptic and look under Epson to see what is installed 

It should be something like [COLOR="#008000"]epson-inkjet-printer-201212w_1.0.0-1lsb3.2[/COLOR]

You don't tell us if you 32bit or 64bit.....Epson supplies both variants.............

---

### Post by SaberCat on 2013-04-20
I discovered that the test .pdf files I was using were the problem. They were all documentation for a single product. Since then I have printed other .pdf files and they have not been blurred. So my message was a false alarm. Sorry. For the blurred .pdf's I found that if I converted them to postscript using pdf2ps they printed OK. Hope that helps others if they run into the same problem... I guess all .pdf files are not equal!

---

