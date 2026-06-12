---
title: "Ubuntu 14 with wireless Epson printer, XP-610"
date: 2015-01-31
forum: Hardware
---

### Post by gabmuks on 2015-01-31
Ubuntu recognizes the printer's model number, but still wont print anything.

There seem to be some settings in the Ubuntu tools/printer section,

but I don't know what they are asking for. I don't know what information

to enter in the Ubuntu tools/printer section. It already has the brand and model number

of my printer listed, so what exactly is Ubuntu looking for to enable this wireless printer?

Thanks for your time.

---

### Post by ajgreeny on 2015-01-31
I can not tell from your description of what you are seeing and doing what is wanted, but it could simply be the local IP address of the printer, eg something similar to 192.168.1.23, which is what mine shows as.

Tell us more about the box names that you need to fill in, or show us a screenshot.

---

### Post by Hugh_Barstead on 2015-02-01
I have the same XP-610 and Ubuntu 14.04 all running on a wireless network. I could not get printing to work until I installed Epson's driver. Yes, Epson provides a Linux driver. Google Epson XP-610 Driver Linux to be directed to the download page. Slick driver, installs easily and provides all functions. 
The same page allows for the download of the scanner driver and the network package for it. I cannot make that work, seems to be missing a dependency or something on my system. I am able to scan with the unit using the XSane image scanning program, but it isn't as useful as what the Epson software should provide.
In any case, install the Epson print driver and print to your heart's content.

Hugh Barstead

---

### Post by Mike_Walsh on 2015-02-01
@ Hugh_Barstead:-

If you're trying to get your scanner working with Epson's 'Image Scan for Linux!', see my post here, in reply to Kimberley2. It should help you to get your scanner working correctly. You may need to substitute your own Epson model:-

[http://ubuntuforums.org/showthread.php?t=2261230](http://ubuntuforums.org/showthread.php?t=2261230)

BTW; DON'T try using Epson's networking package.....it's not what you think it is. I believe it's for connecting Linux AND Windows together in a network with a printer (a form of 'pseudo' SAMBA).To get your computer and scanner to recognise each other in Linux, you'll need to set up their IP addresses manually (the 'ipp' printing protocol); and you may need to assign static addresses to them, since the DHCP server tends to assign random IP addresses to each component, every time you boot up.


Regards,

Mike. ;)

---

### Post by Hugh_Barstead on 2015-02-01
Thanks Mike. I read through the linked thread. Pretty much everything that I have tried. I am not sure we are talking about the same networking package, though. The one I am referring to is bundled on the Epson Linux driver page with the Epson Scan program, and the description reads:

> 
 [network plugin package] 
 This package is optional and only available for certain devices.  Install it if you want to scan via your device's Ethernet or Wi-fi  interface.


As far as I can see, without this package Epson Scan will only look for USB connected scanners. However no matter what I try I simply get the error message "Cannot Communicate With Scanner" and it shuts down. Wireless scanning with the XP-610 works well with my wife's Windows machine, so I know the device supports it.

The printer driver works very well from my Ubuntu laptop. Go figure.

Hugh Barstead

---

### Post by pdc on 2015-02-01
Hi to gabmuks; who started the thread

I see you said [SIZE=4]> but still wont print anything.[/SIZE] so to me that suggests the printing side of things is the main issue for you

Hugh rightly pointed out you need the Epson driver, so if I direct you to it and see if we can get it installed for you?

but firstly; you need to do 3 things if you want a wireless printer to work;

________________

1) **ensure the printer is allowed to communicate inside your network with the router:** the 610 will have a wifi wizard and there is an LCD screen to enter your network password and here is a link [http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&infoType=Videos&oid=227223](http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&infoType=Videos&oid=227223) and the video top-left shows you what to do ......................

2) i[B]nstall the Epson printer drivers
[/B]
3) **register the printer on your system** .............using **ADD A NEW PRINTER** from the Menu/administration/Printing box

_____________________

2) **PRINTER DRIVERS** If you go here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) that is the starting point;

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=23517&DSCCHK=31f0c62eb9b0761d2b2be2840f3d50c5b4c3574a](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=23517&DSCCHK=31f0c62eb9b0761d2b2be2840f3d50c5b4c3574a) is the page for the 610 drivers:

either the epson-inkjet-printer-201308w_1.0.0-1lsb3.2_i386.deb for 32bit or epson-inkjet-printer-201308w_1.0.0-1lsb3.2_amd64.deb for 64bit 

_____________

when you click to download, your system should offer to save or open...........open here means install so take that option;

_________

3) that is the printer driver installed; you may then need to open menu/adminstration/printing and select ADD A NEW PRINTER to get the configuration done

---

### Post by Mike_Walsh on 2015-02-01
Go figure, indeed.

Yes, Epson's support of their hardware under Linux is not all it could be. Okay, I had no problems installing my SX218 (a sort of 'basic' version of their WorkForce business-class printers), and indeed, it uses the same 'filter' driver that many of the WorkForce models employ; but this was only after a fair bit of Googling, and a rather huffy exchange via IM with one of their 'customer support agents', who INSISTED that they 'didn't DO Linux drivers', and then passed me onto a firm called Avasys, who used to develop the 'filters' for them. 

What Epson won't tell you is that Avasys passed control of their repositories BACK to Epson in October 2012; but for a long time, Epson weren't passing this info onto their users. Naughty! Admittedly, the situation's better than it was a year ago, when I started with Linux; but until recently, the only 'drivers' they had on the downloads page were very basic ones. It seems as though they're attempting to gauge the size of the market, and are releasing the more full-featured ones as the user-base grows, and there's more demand for them.

I admit it seems a bit of a pain to install these things in Linux, especially the all-in-ones. You have to download the printer & scanner drivers separately, and then install them separately, rather than the everything at once approach of Windows; but that's more to do with the modular nature of Linux, and being able to install only what you want. If I install this same printer in Windows, I end up with at least half-a-dozen apps that I have absolutely no use for...

Because I don't care what anybody would have you believe; the Linux user-base definitely IS growing. Forum memberships are expanding all the time, and there's more & more mention of Linux, everywhere you look. I've had so much help on here it's untrue, and in my turn, I'm just trying to help new members with various problems. I've installed this particular printer into so many different distros over the last few months, I could in all likelihood do it in my sleep..! And there's a lot of constant enquiries about printers, Epsons among them.....I'm just trying to do my bit! But I'm the first to admit I don't by any means know all the answers...

If you want somebody who knows more than me, [COLOR=#ff0000]pdc[/COLOR]'s your man..! Know a fair bit more about the technical side of things than I do... :)


Regards,

Mike.

---

### Post by gabmuks on 2015-02-13
> **pdc said:**
> Hi to gabmuks; who started the thread

I see you said  so to me that suggests the printing side of things is the main issue for you

Hugh rightly pointed out you need the Epson driver, so if I direct you to it and see if we can get it installed for you?

but firstly; you need to do 3 things if you want a wireless printer to work;

________________

1) **ensure the printer is allowed to communicate inside your network with the router:** the 610 will have a wifi wizard and there is an LCD screen to enter your network password and here is a link [http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&infoType=Videos&oid=227223](http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&infoType=Videos&oid=227223) and the video top-left shows you what to do ......................

2) i[B]nstall the Epson printer drivers
[/B]
3) **register the printer on your system** .............using **ADD A NEW PRINTER** from the Menu/administration/Printing box

_____________________

2) **PRINTER DRIVERS** If you go here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) that is the starting point;

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=23517&DSCCHK=31f0c62eb9b0761d2b2be2840f3d50c5b4c3574a](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=23517&DSCCHK=31f0c62eb9b0761d2b2be2840f3d50c5b4c3574a) is the page for the 610 drivers:

either the epson-inkjet-printer-201308w_1.0.0-1lsb3.2_i386.deb for 32bit or epson-inkjet-printer-201308w_1.0.0-1lsb3.2_amd64.deb for 64bit 

_____________

when you click to download, your system should offer to save or open...........open here means install so take that option;

_________

3) that is the printer driver installed; you may then need to open menu/adminstration/printing and select ADD A NEW PRINTER to get the configuration done

Your instructions worked perfectly PDC. Printer is now working great! Thanks to all of you for your kind help. I will mark thread solved.

---

