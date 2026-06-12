---
title: "Intrepid 8.10 Live CD Issues"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by measekite on 2009-01-02
I have been using Fiesty 7.04 since it came out.  I use it with an Epson 4180 Scanner, a Canon IP4000 printer, an NVidia GeForce 6600 and a ViewSonic DVI monitor.  I use OpenOffice and Gimp amongst other software.


I downloaded and created a Live Cd for Intrepid.   I used it for about 5 hours and here are my comments, issues, and questions.

[U]
**Open Office**[/U]
Open Office 2.41 was included and worked fine but I could not seem to install Open Office 3.  There are dependencey problems.

Has anybody got it to install and work?  How did you do it?  Please provide details?
[U][B]
NVidia 3D Driver[/B][/U]
I went to the section on hardware and drivers and attempted many times to install either 173 or 175 (recommended driver) and the computer would not complete the installation.  I get the dialog box that it tried 6 times and failed.

It says these drivers were tested with Intrepid.  Does anyone know how to correct this situation?  Will I have a problem when I install the OS?  Will my old driver that I have been using with Feisty 7.04 work with intrepid.

[B]_Canon IP4000_
[/B]Under Feisty I had to install CUPS drivers (Canon driver from Japan) as if it was PostScript and Gutenprint so I would print photos under Gimp.  Duplex never worked and I had to install the printer 2 times once for each paper source.

It seems that the Live CD automatically installed a good driver and duplex and paper source works. 

Does anybody know if it will work to print photos (with the proper choices for photo paper like glossy and matte) or do I still have to install Gutenprint and the Canon driver as if it was a postscript driver?

_**Network Drivers**_
On another machine when using Feisty 7.04 and an older Linksys wireless network card I had to go to some file in some folder and make a blacklist entry.  Now I forgot the name of the file and the folder it is in.

Do I still have to do it on that other machine and if so could someone provide me the information of the folder, filname and entry?

_**Installation**_
On that second machine can I just boot Live CD and install directly over Feisty 7.04 by skipping the in between versions or would their be issues down the road and should just back the machine up and install clean?

---

### Post by Partyboi2 on 2009-01-02
> _**Open Office**_
Open Office 2.41 was included and worked fine but I could not seem to install Open Office 3.  There are dependencey problems.

Has anybody got it to install and work?  How did you do it?  Please provide details?[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)
> _**Installation**_
On that second machine can I just boot Live CD and install directly over Feisty 7.04 by skipping the in between versions or would their be issues down the road and should just back the machine up and install clean?                                                       If you are upgrading you cannot skip releases, so you would need to go to gusty>Hardy>Intrepid. If you are not doing this over the net you will need to use the alternate cd to do this. Probably would be alot easier and less time to backup your important stuff and do a clean install of intrepid.

---

### Post by measekite on 2009-01-03
> **Partyboi2 said:**
> [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)
If you are upgrading you cannot skip releases, so you would need to go to gusty>Hardy>Intrepid. If you are not doing this over the net you will need to use the alternate cd to do this. Probably would be alot easier and less time to backup your important stuff and do a clean install of intrepid.


Thanks, Softpedia looks interesting.  It was one of the few resources I did not have.  I even went to the home page and drilled down to your link.  Boy, there was a lot of drilling down and I probably would have missed it since you needed to read all of what was on the screen.  It was there but not obvious.

Thanks for your reply.  Any information on why the drivers for the nvidia locked up on the Live CD.  I hope that the actual install allows me to use the GeForce 6600 driver in the same way as I am currently doing on Feisty.

---

