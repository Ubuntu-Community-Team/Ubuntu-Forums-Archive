---
title: "Printer installation"
date: 2018-01-27
forum: Hardware
---

### Post by nato911 on 2018-01-27
Hello, I am very new to Ubuntu & Linux. I installed Ubuntu 16.04 on my desktop. However,  my printer, Epson wf-2750, is not in the list of printers when I attempt to add it. I have downloaded the drivers but they won't link. So I am asking for assistance to get my printer drivers installed. 

Thank you,
Nato911

---

### Post by pdc on 2018-01-27
so welcome to the Ubuntu forums, nato911;

For the Epson WF-2750, I would go to the Epson Linux Portal [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and if I enter your printer model, I get to here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=68680&DSCCHK=b0b2a070cb35bd28cbff91002aef457c9fc55487](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=68680&DSCCHK=b0b2a070cb35bd28cbff91002aef457c9fc55487) to their printer driver that was released 27th Dec 2017; if you have 64bit Ubuntu, you would need [COLOR="#0000FF"]epson-inkjet-printer-escpr_1.6.18-1lsb3.2_amd64.deb[/COLOR] and if you saved it into your Downloads folder; then if you right-click on the icon; and select "install with gdebi installer ...........", the system should install the drivers; 

there are usually 2 steps:
1) install the drivers
2) register the printer with lpadmin .......... the admin for linux printing (lp) .................

Canon and Brother give one an install script; so it does 1) and 2) where Epson just give you the drivers; 

if you look in your PRINTERS folder; and delete any existing entries; then download the above driver ...... it should ............ install the driver and that should trigger a registration with lpadmin; if it doesn't the PRINTERS folder has an ADD button top left for you to ADD a new printer .. your WF-2750

---

### Post by panos69 on 2018-03-08
After having tried all the above with no luck,i managed to install the EPSON DX9400F using [COLOR=#000000][FONT=Verdana]"sudo apt install cups". 



[/FONT][/COLOR]

---

### Post by pdc on 2018-03-09
Hi panos69;

welcome to the Ubuntu forums; 

that is a venerable printer you have there; well done to have it still working well; and well done to Epson for making a good product that is still working 10 yrs later; 

and well done to Epson; who supply a driver; [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=68680&DSCCHK=b0b2a070cb35bd28cbff91002aef457c9fc55487](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=68680&DSCCHK=b0b2a070cb35bd28cbff91002aef457c9fc55487)

for a 64bit Ubuntu, you would need [COLOR="#0000FF"]epson-inkjet-printer-escpr_1.6.18-1lsb3.2_amd64.deb[/COLOR] ..... which is what Epson recommend for the WF-2750 too 

_____________

I was unclear what you were telling us in your post panos: it seemed you were saying you tried to install the driver for the wf-2750; for your DX9400F ........ was that what you were saying? ..... and it didn't work?

---

