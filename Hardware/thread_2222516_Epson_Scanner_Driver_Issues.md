---
title: "Epson Scanner Driver Issues"
date: 2014-05-06
forum: Hardware
---

### Post by Paper Pusher on 2014-05-06
I currently my computer to 14.04 and I need to have my scanner working. So I went to Epson's page and went to their driver downloads and typed the the model I have (Perfection V100) and I selected a driver download (iscan-plugin-gt-s600_2.1.2-1_i386.deb). After downloading this I clicked on it in order for it to open. Upon clicking on it, the software center opened up but after a few minutes of waiting, the software center went no further than the home page. I tried to download some RPM files to see if there was a difference and upon clicking on them, the software center opened and went further to tell me that it was a invalid file for my device. My computer is 32-bit, dual-cote atom.

---

### Post by pdc on 2014-05-11
so I would go here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and tap in 100 and that takes me to here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27729&DSCCHK=dad2cb5b45435c09005b7aca852ad8acb85329f5](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27729&DSCCHK=dad2cb5b45435c09005b7aca852ad8acb85329f5)

and you need 2 things

1) the data package installed first (and it is BOTTOM of the list ...............)       [COLOR="#008000"]**iscan-data_1.28.0-2_all.deb**[/COLOR]
2) [COLOR="#008000"]iscan_2.29.3-1~usb0.1.ltdl7_i386.deb[/COLOR]        (as you are 32bit and have a recent kernel .................[COLOR="#DDA0DD"]ltd7[/COLOR] for recent ....................[COLOR="#DDA0DD"]ltd3[/COLOR]     for ancient )

If you elect to OPEN as you click to download, gdebi installer should leap in and offer to help............. accept it if offered...................

that should really get you set up .............

_____________________________________________________________

this page [http://download.ebz.epson.net/faq/linux/faq_ls_00002.html](http://download.ebz.epson.net/faq/linux/faq_ls_00002.html)

explains about the data package and a network package that some may opt for ..............

_______________

if you subscribe to a thread, you can more easily follow it ......options a few lines down ...............

---

### Post by sammiev on 2014-05-11
> **pdc said:**
> so I would go here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and tap in 100 and that takes me to here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27729&DSCCHK=dad2cb5b45435c09005b7aca852ad8acb85329f5](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27729&DSCCHK=dad2cb5b45435c09005b7aca852ad8acb85329f5)

and you need 2 things

1) the data package installed first (and it is BOTTOM of the list ...............)       [COLOR="#008000"]**iscan-data_1.28.0-2_all.deb**[/COLOR]
2) [COLOR="#008000"]iscan_2.29.3-1~usb0.1.ltdl7_i386.deb[/COLOR]        (as you are 32bit and have a recent kernel .................[COLOR="#DDA0DD"]ltd7[/COLOR] for recent ....................[COLOR="#DDA0DD"]ltd3[/COLOR]     for ancient )

If you elect to OPEN as you click to download, gdebi installer should leap in and offer to help............. accept it if offered...................

that should really get you set up .............

_____________________________________________________________

this page [http://download.ebz.epson.net/faq/linux/faq_ls_00002.html](http://download.ebz.epson.net/faq/linux/faq_ls_00002.html)

explains about the data package and a network package that some may opt for ..............

_______________

if you subscribe to a thread, you can more easily follow it ......options a few lines down ...............

+1 
Use this site for all Epson printer and scanner drivers.

---

