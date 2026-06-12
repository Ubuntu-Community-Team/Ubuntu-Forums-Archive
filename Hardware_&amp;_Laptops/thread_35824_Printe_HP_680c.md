---
title: "Printe HP 680c"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by rasousa@gmail.com on 2005-05-20
Hi,

my printer (hp 680c) is detected by Ubuntu, but only print crazy characters. 
This printer is not listed in the "hardware compatibility list", but is detected. 

Thanks for help!

Rogerio

---

### Post by David Haas on 2005-05-20
Rogerio--After selecting New Printer and then your printer in the printer GUI (System>Administration>Printing), you must select the PPD file for your printer in this GUI. To do so, click through the file system to reach the PPD file(s) for your HP 680C. I see it listed in the HP directory located at /usr/share/cups/model/foomatic-ppds/HP. Three are present: 
HP-DeskJet_680C-cdj670.ppd.gz
HP-DeskJet_680C-hpijs.ppd.gz
HP-DeskJet_680C-pcl3.ppd.gz

I believe the hpijs is written by HP itself and distributed free to the Linux community. After selecting this file (the GUI says "open" to select it), you should see an unzipped copy in /etc/cups/ppd -- and your printer should work. Sometimes, it's best to erase the already selected printer and begin over by clicking on "New Printer."

David

---

