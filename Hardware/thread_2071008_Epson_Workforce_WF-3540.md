---
title: "Epson Workforce WF-3540"
date: 2012-10-14
forum: Hardware
---

### Post by aletroux on 2012-10-14
I have just bought this printer in a hurry as our previous printer broke down rather suddenly. It seems to be a brand new model. Unfortunately I cannot find any drivers for it anywhere - can anybody advise on what I can do to get this printer to work with my Ubuntu 12.04?

My previous two Epson printers worked perfectly and easily with Linux so it didn't cross my mind to check compatibility beforehand. ](*,)

---

### Post by pdc on 2012-10-14
how about go here?

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

.......the default search site for Epson drivers is now

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

......let us know how it goes................

---

### Post by aletroux on 2012-10-14
Hi yes, thank you, I've now downloaded the drivers from there and they work perfectly.

The website you mentioned was the first place I looked this morning, but for some reason I couldn't find the drivers on there (the search returned no results). I've now worked out what I did wrong. For the benefit of anybody reading this  thread:  search for WF-3540 instead of WF3540 like I did. The dash really makes a difference!

---

### Post by pdc on 2012-10-14
good;

enjoy

---

### Post by Albert Seminatore on 2013-01-28
> **pdc said:**
> how about go here?

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

.......the default search site for Epson drivers is now

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

......let us know how it goes................

I just installed a NEW Epson WF-3540 all in one printer on LinuxMint Cinnamon system.  Installed the software stated above as well as a recommended scanning software driver.
  Wireless works fine.  Print test page works fine.  Print single sided page from any Doc. Fine.  Scan from the flatbed scanner is fine.
  PROBLEM:  Can NOT print double side even though a select double sided when printing the document as well as having set double sided on the printer.
  PROBLEM:  Can NOT scan from the ADF.  It starts to load a page and then I get an error mesg.  Can't start scanner.

  Is there another piece of software I need to load to be able to use these features?    My HP6500 worked fine doing these things until the duplexer started grinding gears.

Any Help would be appreciated.........  Al
confused:[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by pdc on 2013-01-28
Hi Albert; 

so I would start here

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

and enter 3540 and get to here

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

and it lists both printer drivers: for the printer side of the MFD and a scanner driver for the scanner side .............

.........I see you can download either the [COLOR="Blue"]ESC/P Driver (full feature)[/COLOR] or the [COLOR="Magenta"]ESC/P-R Driver (generic driver)[/COLOR]

and if I were to go for the [COLOR="Blue"]full feature driver[/COLOR] I would click and go here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71)

and you don't tell us if you are 32bit or 64bit ....

if 32bit you would have downloaded and installed the [COLOR="SeaGreen"]epson-inkjet-printer-201212w_1.0.0-1lsb3.2_i386.deb[/COLOR]

........to help us.......could you copy and paste this command

> [COLOR="Red"]sudo dpkg -l | grep epson[/COLOR]

and copy and paste the results back; so we can see what is installed ..

(*for copy and paste in a terminal, if you use the top line: MENU then PASTE ........ it is often easier....*)

_______________________________________________________________

.......so for the scanner for this device you need to download 

> the [COLOR="Blue"]core[/COLOR] package & the [COLOR="Blue"]data[/COLOR] package

....... and 1) install the [COLOR="Blue"]DATA[/COLOR] PACKAGE 

....... and 2) the [COLOR="Blue"]CORE[/COLOR] PACKAGE

......in that order ..............

so 1) the [COLOR="Blue"]data[/COLOR] package is **[COLOR="SeaGreen"]iscan-data_1.21.0-1_all.deb[/COLOR]** and is found at the very bottom of the page of packages that show; when one clicks the ACCEPT button............

.....when you click to download, gdebi installer should jump in and offer to help:let it ...........

and 2) for the [COLOR="Blue"]core[/COLOR] package, if 32bit, download and install the [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.[COLOR="Magenta"]ltdl7[/COLOR]_i386.deb
[/COLOR]
you will notice the [COLOR="Magenta"]ltd7[/COLOR] as part of the file name: [COLOR="Magenta"]ltd7[/COLOR] is for new kernels so use that 

......if you paste back the answer I asked for in part 1

.and I hope installing the scanner packages should get the scanner working

---

### Post by fpeelo on 2013-02-24
> **Albert Seminatore said:**
> PROBLEM:  Can NOT print double side even though a select double sided when printing the document as well as having set double sided on the printer.

Hi

Are you printing from LibreOffice?

I have a WF-3520 and it also does not print duplex when I print from LibreOffice. But if I print a web page from Firefox, or if I print a PDF, I can print duplex. I think this is a LibreOffice bug because it does not seem to affect other programs.

Frank

---

### Post by sanitychecked on 2013-05-16
Greetings from the future: May 2013, to be exact.

Unfortunately, I cannot recommend (and have to warn against) the WF-3540 multifunction with at least Ubuntu 13.04.

Threads like this and glowing reviews on Linuxprinting.org etc. suggested that all device features just might be working by now.  Printing does work fine, and with excellent speed and quality, using the proprietary driver which Ubuntu does automatically identify and download (do remember to be very patient if you have other installations queued in the Software Center).

Trouble is, scanning is a sad mess.  The proprietary scanner driver, when it works (required either a 'boy I sure do like crossing my fingers and running proprietary software the vendor halfway disowns as root' moment or an unplug/replug of the printer or both) consists of essentially a standalone app.  It is slightly above "shovelware" in quality and would probably be fine for photo scanning, but the drivers do not expose enough to SANE to permit gscan2pdf or other common, daily, *essential* office utilities to select to feed from the ADF.  Which renders the device useless for local document scanning.  In fact, gscan2pdf won't even -stop- scanning from the flatbed after the first 'page', so even flatbed scanning will be a race to cancel the scanning loop and delete all the duplicate pages it's created.  The device appears as "Epson (Unknown Model)" with no "Device-Dependent Options" where the ADF and so on choices would be for my departed HP.

(The "Epson Connect" feature, which requires Windows or Mac software to set up even though it appears to then be a standalone feature when the device is actually networked rather than on USB, may be a workaround, but apparently bounces all your scans through Epson's servers even if you choose delivery to your own email.  Privacy?  Basic functionality without depending on 3rd-party servers?  That's 20th century talk.  It's *Cloudy*, people, get *with it* and tweet that you like it, bro.*  Apparently if you'd prefer delivery to an actual cloud service rather than email, your choices are limited to Box, Dropbox, Evernote, or Google Drive.  No Ubuntu One, no Amazon, no... whatever else you hep cats are using these days.)


Two more nails in the annoyance coffin:
[LIST]
[*]As with pretty much every printer, no combination of paper size settings in the CUPS configurator and envelope feed options in LibreOffice will actually result in an address correctly positioned on an envelope centered in the rear envelope feeder.  A feeder which also has the 'feels neat the first time, until you immediately realize this is a terrible idea' feature of motorizedly grabbing your paper and refusing to let go without passing it through to the front of the printer.  Accidentally insert something with a staple or other obstruction?  I haven't yet, but good luck recovering from that.
[/LIST]


[LIST]
[*]Nearly every error condition on the printer display 'hides' another error to 'insert paper in cassette to receive faxes' or such behind it.  When the cassette is full and the printer knows it.  Dismissing these gets old fast.
[/LIST]


I don't want to particularly rail into Epson here - as their support department reminds me as I provide constructive, if entertainingly frustrated criticism, they **Do Not Support Linux**, and those drivers they commissioned and offer for download to give the impression of Linux support and convince you to buy their product are **Not Support, okay?  They're just a thing you can see on the website, that maybe gives the impression that something might work with Linux, but Linux is Not Supported** - but I do want to get it out there that _this is just not a good device for Linux_ unless you're only after a good printing feature glued to an acceptable standalone fax feature.  Which is slightly confused about whether it needs paper loaded on top of its paper.  [Given that support keeps reminding me that it's Not Actually Supported, I have to say that Epson concedes this, though not so much in the pre-sales material.]


So - caveat emptor.  This was a thread that convinced me the minor issues would be surmountable, but as of now, they're not, and the scanner software bears a copyright date somewhere around 2008-2010, so I don't think this is a high priority for Epson or their software partner who spent more time doodling a penguin with its face smooshed on a scanner to fill a blank area in their "Image Scan!" UI than properly exposing functionality to SANE.  (Please do PM me if anyone other than HP does make an inkjet MFC that plays fully nice with Linux.  My experience with HP on the Linux/*NIX software end has always been surprisingly good with about 80% of promised features working for any given product, but the 'we figured out we could charge more for ink than enriched uranium' practice means there's no savings in not skipping straight to laser.. unless you occasionally want to print an actual photo, in which case you maybe want to start looking for a tall building with no fence around the rooftop.)



*This may need a sarcasm tag.  Askubuntu.com is apparently promoting "Podcast #47 – Do You Even Twitter Bro?" as I type.  Poe's Law means I can't tell, and I don't want to find out...

---

### Post by dolive on 2013-12-06
I'm running Ubuntu 10.04LTS and the iscan install is broken.   Install of iscan-data works fine.   But when I try to install iscan_2.29.2-1 I get an error message claiming that the libltdl3 dependency is not satisfied.  It wants >= 1.5.2-2.   But I've got 1.5.26-1ubuntu1 installed.   Somehow the dependency doesn't recognize the library I have installed.

When I tried using stock Ubuntu scanning packages (using sane) I get an Error Communicating with Scanner message and the WF-3540 goes into some brain dead state where all the lights start flashing.   You have to cycle the power to get it to come back to life.

---

### Post by DigiAngel on 2014-01-30
dolive, that's exactly what I'm dealing with now...did you ever get a fix for this?

---

### Post by DigiAngel on 2014-01-30
I installed:
iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb
iscan-data_1.26.0-1_all.deb

And now it works...woot

---

### Post by tarnall on 2014-04-15
I've been having a problem installing the driver for my WF-3540.  I get a whole list - which one do need?  Ubuntu 13.10  What I have are two HDD in my computer, Windows 7 on one and Ubutnu on the other. Ubuntu installed a booter, grub.  The printer works fine in Windows.  PC 64 bit, i7, 6 Gb memory

epson-inkjet-printer-escpr-1.4.0-1lsb3.2.i486.rpm	1.75 MB	
epson-inkjet-printer-escpr_1.4.0-1lsb3.2_i386.deb	2.09 MB	
epson-inkjet-printer-escpr-1.4.0-1lsb3.2.x86_64.rpm	1.75 MB	
epson-inkjet-printer-escpr_1.4.0-1lsb3.2_amd64.deb	2.11 MB	
epson-inkjet-printer-escpr-1.4.0-1lsb3.2.src.rpm	1.79 MB	
epson-inkjet-printer-escpr-1.4.0-1lsb3.2.tar.gz	1.85 MB	

Thanks for any input!
Terry

---

### Post by pdc on 2014-04-15
Hi Terry; so you are using ubuntu so you need a debian package; 

you don't tell us if 32bit or 64bit:                 32bit you would need [COLOR="#008000"]epson-inkjet-printer-201212w_1.0.0-1lsb3.2_i386.deb[/COLOR] and 64bit ..................[COLOR="#008000"]epson-inkjet-printer-201212w_1.0.0-1lsb3.2_amd64.deb[/COLOR]

and for the scanner side;  you need a **[COLOR="#0000FF"]DATA[/COLOR]** package and [COLOR="#0000FF"]scanner[/COLOR] package: DATA is [COLOR="#008000"]iscan-data_1.27.0-1_all.deb[/COLOR] (install before main scanning package) and then you need a debian [COLOR="#EE82EE"]ltdl7[/COLOR] package ie either [COLOR="#008000"]iscan_2.29.3-1~usb0.1.ltdl7_i386.deb[/COLOR] or [COLOR="#008000"]iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb[/COLOR]

([COLOR="#EE82EE"]ltdl3[/COLOR] is for really old kernels)

scanning link here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27427&DSCCHK=088aed7d31a621dc6c3ebfbefd9d4dcce571416a](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27427&DSCCHK=088aed7d31a621dc6c3ebfbefd9d4dcce571416a)

---

### Post by skierpage on 2014-07-13
@sanitychecked, yours is the greatest post I've seen on Ubuntu Forums. Accurate, informative, zero fanboi, funny. You win the interwebz.

I bought one of these, plugged it in to wired Ethernet, ran setup on its front panel to give it a network address.

Ubuntu 14.04's Printers > Add > Printer found this printer on my network, but wasn't able to find the right driver for it after a long delay searching.  So I followed the link at [http://www.openprinting.org/printer/Epson/Epson-WF-3540_Series](http://www.openprinting.org/printer/Epson/Epson-WF-3540_Series) , downloading the "**x86 64 bit:** [1.0.0 (DEB for LSB 3.2)]("http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/main/binary-amd64/epson-inkjet-printer-201212w_1.0.0-1lsb3.2_amd64.deb")", installed the package, and when I re-ran Printers > Add > Printer it used that driver. Sad that the driver is stuck at version 1.0 from 2012

So far it's printing OK. I haven't tried scanning or faxing. I note a minor HTML escaping bug: the Printer Properties > Printer Options dialog displays the HTML tags in "<b>Paper & Quality Options</b>".

---

