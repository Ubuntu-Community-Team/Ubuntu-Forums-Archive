---
title: "epson 235w"
date: 2013-03-09
forum: Hardware
---

### Post by witblits1970 on 2013-03-09
i have the above printer that also has a scan facility. how do i get it to scan? i have installed xsane, skanlite, simple scan and scanner util but it keeps telling me i have no scanner installed. thing is i can print with no issues and seeing its a all in one it should work or at least i thought so

---

### Post by pdc on 2013-03-11
Epson provide linux support

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

if I type in 235, I get what is in the thumbnail

You don't tell us if you have 32bit or 64bit but clicking on the core package and data package button gives this

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435)

**[COLOR="#EE82EE"]YOU MUST INSTALL THE DATA PACKAGE FIRST[/COLOR]** ..........[COLOR="#008000"]iscan-data_1.22.0-1_all.deb[/COLOR] .............................as Ubuntu uses debian packages

.......*how to install a debian package;* right-click on its icon after download, and select "install with gdebi installer" is one option................

then if 32bit you need [COLOR="#008000"]iscan_2.29.1-5~usb0.1.ltdl7_i386.deb[/COLOR] .....note the[COLOR="#EE82EE"] ltd7[/COLOR] component.........[COLOR="#EE82EE"]ltd7[/COLOR] is for newer kernels Epson says..................

there is also a network plugin package[COLOR="#008000"] iscan-network-nt_1.1.0-2_i386.deb[/COLOR]

**[COLOR="#EE82EE"]FOR INSTRUCTIONS[/COLOR]** on running[COLOR="#0000FF"] iscan [/COLOR]and more trouble-shooting, if you download the pdf file [COLOR="#008000"]userg_revQ_e.pdf[/COLOR] from here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435)

to get it all to run, Epson say to type

> [COLOR="#FF0000"]iscan[/COLOR]

in a terminal............you can always create a launcher afterwards if all is good........google on how to do that if you don't already know

let us know how it all goes for you; best wishes

---

