---
title: "Printer printing gibberish"
date: 2014-06-01
forum: Hardware
---

### Post by Randomtastic on 2014-06-01
Hello all,

I bought a new Epson WF-3520 and successfully connected it over wifi. My Ubuntu 14.04 (64 bit) computer recognises the printer with no problems. It then tries to install the driver, only to then ask again if I confirm that it's the driver I want to install. It then asks what my printer is for some unknown reason, then once again asks if I want to install the driver. Eventually the printer is added in the settings but when I go to print a test page or a document, I get ASCII gibberish.

I tried installing the driver package (epson-inkjet-printer-201212w), the .deb package in amd 64 bit form, and I get the same problems. I tried uninstalling, then reinstalling through the terminal. Same problem. I tried 32 bit, I tried get-update, uninstalling and reinstalling each time. And now I'm here...

Can anybody help me with this please? Thanks

---

### Post by sammiev on 2014-06-01
Get your drivers from [here]("http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult") and give it another go. In the search use WF-3520.

---

### Post by Randomtastic on 2014-06-01
Thanks Sam, I'll write out my progress:

1) Got 5 results for Linux, chose the full feature driver ESC/P.

2) Chose Debian AMD 64 option.

3) Opened the package, Ubuntu Software Center opened.

4) Installed package.

5) Two options appeared for connection when I tried to add the printer - AppSocket/JetDirect and IPP, gone with AppSocket/JetDirect but please advise if I've made a mistake.

6) New printer menu appeared, says that a package is available for download - the epson 201212w package. I can also choose the local driver option. Before I would pick the former but surely I've already installed that package? Should I continue or choose local driver?

---

### Post by sammiev on 2014-06-01
I would have deleted the one you first had trouble with and then install the one you just downloaded. Seems like your on the right path.

---

### Post by Randomtastic on 2014-06-01
I did, that's what seems strange to me. I uninstalled the package through the terminal. Then I reinstalled as per your instructions - the install button rather than a reinstall button was available in the Ubuntu Software Center, confirming that the package was definitely gone before I installed it. But then when I go to add the printer, the set up gives me the option of installing the package I just installed... which seems counterintuitive.

---

### Post by sammiev on 2014-06-01
> **Randomtastic said:**
> I did, that's what seems strange to me. I uninstalled the package through the terminal. Then I reinstalled as per your instructions - the install button rather than a reinstall button was available in the Ubuntu Software Center, confirming that the package was definitely gone before I installed it. But then when I go to add the printer, the set up gives me the option of installing the package I just installed... which seems counterintuitive.

I never had the reinstall show up when I did mine. The only choice I had was to install which I did and all worked. If you end up with the same problems you can still download the other driver from the same site and try that one.

---

### Post by randomtastic2 on 2014-06-01
I narrowed the problem down - seems the printer was set to HP driver by default. But when I try to select an Epson Workforce driver, all I see are the 7000 series printers and some other ones in the hundreds. The package is definitely installed, is there a way to manually select the driver?

---

### Post by fkkroundabout on 2014-06-01
gibberish sounds curious, am tempted to see a picture

---

### Post by pdc on 2014-06-02
> 4) Installed package.

5) Two options appeared for connection *[COLOR="#EE82EE"]when I tried to add the printer[/COLOR]* -

..........by rights, the Epson install should have created a driver; and created an entry in CUPS;

if you click on this link [http://localhost:631/printers/](http://localhost:631/printers/)    ..........you should see at left [COLOR="#0000FF"]Queue Name[/COLOR]      ..........and at right **Make and Model** ........and the latter should spell out the driver (epson-inkjet-printer-201212)

........how many epson entries do you have please? can you do a screenshot?

____________________

if I re-trace the steps for the driver; seems to me one would go to here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) 

and type in 3520 and you get to here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71) and you can download [COLOR="#008000"]epson-inkjet-printer-201212w_1.0.0-1lsb3.2_amd64.deb[/COLOR]           and when you click to download, the **OPEN** option should allow one to "open with gdebi installer" and that of itself should create the printer entry;

seems like that is not happening and the question is why

_________________________________

> The package is definitely installed

so in a terminal. what does 

> [COLOR="#FF0000"]dpkg -l | grep epson-inkjet-printer[/COLOR]

give; if you copy and paste this command into a terminal please

---

### Post by sammiev on 2014-06-02
> **pdc said:**
> ..........by rights, the Epson install should have created a driver; and created an entry in CUPS;

if you click on this link [http://localhost:631/printers/](http://localhost:631/printers/)    ..........you should see at left [COLOR="#0000FF"]Queue Name[/COLOR]      ..........and at right **Make and Model** ........and the latter should spell out the driver (epson-inkjet-printer-201212)

........how many epson entries do you have please? can you do a screenshot?

____________________

if I re-trace the steps for the driver; seems to me one would go to here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) 

and type in 3520 and you get to here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71) and you can download [COLOR="#008000"]epson-inkjet-printer-201212w_1.0.0-1lsb3.2_amd64.deb[/COLOR]           and when you click to download, the **OPEN** option should allow one to "open with gdebi installer" and that of itself should create the printer entry;

seems like that is not happening and the question is why

_________________________________



so in a terminal. what does 



give; if you copy and paste this command into a terminal please

and how many other printer drivers that show installed like HP as well. You may have the correct one installed but have the wrong one chosen.

---

