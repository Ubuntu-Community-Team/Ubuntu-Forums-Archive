---
title: "Adding hardware"
date: 2014-04-01
forum: Hardware
---

### Post by rbmoler on 2014-04-01
I'm still a novice user of Ubuntu, so I may be sticking my foot in where it doesn't belong, but I thought I'd ask.

Ubuntu is working fine for me.  I've gotten my Samsung wireless laser printer up and running.  When I look at printers it claims that it's supports two sided printing, but I've never gotten it to do that in an application such as printing an article from the Washington Post Online.  That's a minor issue.

I also have an Epson Artisan 837 wireless all-in-one.  It's installed, but operates in only its very basic mode. I can print in color on 8.5x11, but nothing else is accessible, no photo printing, no two sided printing, no CD printing, no scanning no high resolution printing.

I went through the process of checking if any of that was possible.  There's a website that gives information about printers and scanners which claims that there is a driver (wrong terminology in linux I think?)  that is "complete."  I downloaded it then realized I hadn't a clue about how to use it.  I found a posting from someone who was trying to install a Canon scanner and that process looked to be horrendous.  I assume the same would be true of my Epson v300 scanner and the epson all-in-one.

Last thing:  Will the same difficulties present themselves getting my Logitech camera  and a little simple memory card reader installed and working?

Thanks for your advice

---

### Post by grahammechanical on 2014-04-01
I do not have a printer but from the little reading I have done when thinking about buying a printer it seems that basic printing is possible but getting some printers and all-in-one printer/scanners working and wirelessly at that can be difficult due to the lack of drivers (correct term) being supplied by the manufacturers. 

Some printers are better supported than others. And improved drivers come with the latest versions of Ubuntu? Which version are you running? You might get better results with 14.04 when it comes out.

This thread might help. Sadly the original poster never reported the results of the help given.

[http://ubuntuforums.org/showthread.php?t=2088526](http://ubuntuforums.org/showthread.php?t=2088526)

Have you thought about pluging in the printer/scanner and then running the additional Drivers utility?

Regards.

---

### Post by rbmoler on 2014-04-01
I using Ubuntu 12.04.  I'm aware of the new version being released soon in a LTS version, so I'm likely to upgrade fairly soon.  Maybe things will be better then.  I'm not completely inept - I did get my second HD to mount at boot up.  It holds my mozilla profiles and all the files of things I've written using Libre writter and some data bases in Adabase that I use on Win XP so I can switch from one to the other as my OS and have everything important handy.

With considerable help I now run an ancient DOS based database program in DosBox and have configured it to start when I open DosBox.  So that is preserved intact for either OS.

I can do what I need by saving files in the common HD and printing, scanning etc in XP.  Bit of a nuisance, but workable.

In principal, I suppose I could use a virtual box to install XP and do it in Ubuntu.

---

### Post by mastablasta on 2014-04-02
how was the samsung printer installed? did you use a PPA? : [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

depends on camera model and card reader model. if you buy the kind that has linux support, then you just plug it in.

---

### Post by rbmoler on 2014-04-02
I'm definitely exhibiting my ignorance here, but I don't know what PPA stands for.  I've seen it a few times, but haven't seen a definition.  I just looked it up and no I didn't us a PPA to install the Samsungs.

Actually I have two Samsung printers installed.  One is local (Samsung 1740) - connected to my parallel port so I can print my old DOS program.  The other is a newer Samsung (M2825), wirelessly connected through my home network.  Both printers showed up in the list of printers in ubuntu 12.04.  Ubuntu found both printers and had the drivers for them  so I had essentially nothing to do.

---

### Post by rbmoler on 2014-04-04
Nevermind.  It was all my ignorance of how Ubuntu handles printers and their capabilities.  Still doesn't do two sided though even though the printer is capable of it.

Anyway - issue resolved.

---

### Post by pdc on 2014-04-05
pleased the issue is resolved;

for anyone following; for a printer driver for an Epson for linux, one goes here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

when I type in 837 I get the thumbnail as below: 

so there is a full feature **[COLOR="#008000"]printer driver[/COLOR]**; and a **[COLOR="#008000"]scanner driver[/COLOR]**;

clicking on full feature printer driver takes you to a choice window: for ubuntu one needs a debian package; either 32bit or 64bit as per one's system; so for 32bit one would download [COLOR="#008000"]**epson-inkjet-printer-201112w_1.0.0-1lsb3.2_i386.deb**[/COLOR] and if one clicked to open with gdebi installer as it was downloaded, that would install it in one's system; and the printer should thus be configured;

_____________

for the scanner driver, a [COLOR="#008000"]scanner package[/COLOR] AND a [COLOR="#008000"]data package[/COLOR] are downloaded; the [COLOR="#008000"]data package[/COLOR] must be installed first:

again, for the scanner driver, epson have to offer a range of packages: rpm and deb; 32bit and 64bit flavours; and ltd3 packages for older kernels!! ............and ltd7 for newer kernels !!

so for a 32bit ubuntu system one would go here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27427&DSCCHK=088aed7d31a621dc6c3ebfbefd9d4dcce571416a](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27427&DSCCHK=088aed7d31a621dc6c3ebfbefd9d4dcce571416a)

and download and install firstly the [COLOR="#008000"]iscan-data_1.27.0-1_all.deb[/COLOR] from the bottom of the page ..........and then ......................[COLOR="#008000"]iscan_2.29.3-1~usb0.1.[/COLOR][COLOR="#DDA0DD"]ltdl7[/COLOR][COLOR="#008000"]_i386.deb[/COLOR]

............again if one selects " open with gdebi installer" on beginning download, both should be installed easily.......... I have highlighted the ltd7 component of the scanner package; to show it more clearly

---

