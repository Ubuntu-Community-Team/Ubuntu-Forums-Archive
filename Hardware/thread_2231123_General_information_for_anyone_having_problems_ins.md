---
title: "General information for anyone having problems installing printer drivers in Trusty T"
date: 2014-06-23
forum: Hardware
---

### Post by Mike_Walsh on 2014-06-23
Greetings, one and all.

Many of you who are new to Ubuntu (like myself), who have recently installed Ubuntu 14.04 (Trusty Tahr), and are having problems installing your printer drivers.....please read on.

Like the majority of you, I too tried to install my printer driver by clicking on 'Settings>Printers>Add', and following the instructions through.

Like me, you've probably found that the installation gets stuck halfway through, and refuses to go any further.

If you, too, are in this same boat, please read on; this work-around may do the job for you, too.

My printer is an Epson; they are, unfortunately, known for being a bit awkward under Linux, anyway. I Googled the name of the driver (obtained from the driver search BEFORE the installation seized up), and, from the results, found this page:- 

[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

If you visit this site, you can enter your printer make & model, and then select 'show this printer'. The following page will give a list of drivers; if you have a 32-bit version, you want the 'x86 32 bit'; if, like me, you have the 64-bit version, make sure you select the 'x86 64 bit'.

In BOTH cases, you will want the DEB version.

Click on this, and save to your Downloads folder.

Go into Downloads, and right-click; open with Ubuntu Software Centre.

It should come up like anything else you install through the Software Centre; click on 'Install', authenticate when asked for your password, and it will do its thing.

And that SHOULD be that!

I am not making ANY guarantees that this will definitely work for anybody else; but if you're tearing your hair out, like I was, it's got to be worth a try. It certainly seems to work for Epson printers, and basically installs the correct software for proper operation under CUPS (the Common Unix Printing System); for those new to Linux, it is based on UNIX, which is a very much older, and well-established O/S.

Hope this helps somebody else.

Mike Walsh.

PS: This does NOT, however, seem to enable the scanner portion of the 'all-in-one'; I understand that this requires further drivers, and adding some new repositories through the terminal; I will update this thread when I have discovered how to do this!

The drivers in question seem to originate from the Avasys site. However, upon further investigation, Avasys appear to have stopped supplying Linux printer drivers sometime back in late 2011.....therefore these are some years old. But then, so's my printer; as long as it all works, does it really matter?

---

### Post by pdc on 2014-06-24
Hi Mike; glad it all worked for you:

Epson have a linux download page [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) 

so for the XP-211 for example, 

it then lists the printer and scanner drivers: for scanner drivers, it takes you here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27729&DSCCHK=dad2cb5b45435c09005b7aca852ad8acb85329f5](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27729&DSCCHK=dad2cb5b45435c09005b7aca852ad8acb85329f5)

and Epson say: install the [COLOR="#EE82EE"]DATA PACKAGE[/COLOR] first; then the core scanning package: Avasys was a name from before 2011 or thereabouts; 

______________

clicking on the OpenPrinting as you suggest; takes one to the same point as the above; **going direct to Epson** though gives you the scanner driver access as well as printer driver; seems to me usb connect for scanning works; network requires editing the epkowa.conf file etc

---

### Post by Mike_Walsh on 2014-06-24
Hi, pdc.

Well, I know several people pointed me in the direction of the Epson Linux download page. But every time I went to it, or used the 'Choose Printer' & 'Choose Operating System' options on the page leading to it, I could never get the page to display any driver packages at all! It would only ever list an empty search area, with 'Nothing to display' on it.

Now, maybe this has something to do with the DNS secure servers I'm on...I don't know. When I was running XP (sorry for swearing!) I was using Comodo's Firewall; and part of the condition for using it was to route everything through THEIR secure DNS servers. I would have thought, however, that by replacing XP with Ubuntu 14.04, everything would have been reconfigured...

Anyway, to return to the plot. Through researching things, I soon realised that Avasys were the people who for long enough had supplied the Epson Linux drivers; but back in late 2011, they stopped providing the download. They handed over the download capability to Epson themselves. I had an online chat with a very nice lady from the Epson UK customer support section, who quickly informed me that Epson don't provide a Linux driver...and kindly directed me to the Avasys site. Upon reading the news section on their homepage, I very soon discovered they had handed responsibility back to Epson.....who were at pains to point out that they don't actually DO a Linux driver...! *grrr...*

Talk about about being passed from pillar to post!

Have a look at this; it merely confirms what I've just said:- [http://avasys.jp/eng/linux_driver/news/id001092.php](http://avasys.jp/eng/linux_driver/news/id001092.php)

So, I jotted down the name of the driver selected during the normal setup process (before it grinds to a halt halfway through!) and Googled it directly. That was how I found the Openprinting website; and upon closer inspection, realised that their version of the required driver must have been obtained from Avasys BEFORE they stopped providing it!!

Like I said, though, the printer itself is about 5 years old, so driver and printer are probably about the same age. I don't really care as long as it now works. Kinda makes you wonder why I can't get a result through Epson's search page, and yet everyone else seems to be able to... I must admit, the site seems to take forever to load ( and we have a good broadband speed; 60 Mb/sec down, around 20 Mb/sec up); that's GOOD by UK standards, yet more often than not, the browser 'times-out' before the site has condescended to load!

Mystifying.

I agree, it's a bit of a 'round-the-houses' solution, but it works.....for me, at least. I can't be the ONLY one having trouble with the Epson site..!

Mike.

PS: I'll have a look at your link for the scanner drivers page.....see if THAT brings any joy! Thanks for that.

---

### Post by sammiev on 2014-06-24
I'm like pdc,

Epson have a linux download page [http://download.ebz.epson.net/dsc/se...search/?OSC=LX](http://download.ebz.epson.net/dsc/se...search/?OSC=LX) 

It works great for me.

---

### Post by Mike_Walsh on 2014-06-24
Hi again, pdc. 

Just tried your link to the scanners download page...and this happened (in fact, this happened several times before, though I did eventually get the site to load):-

"The connection was reset

The connection to the server was reset while the page was loading.

    The site could be temporarily unavailable or too busy. Try again in a few moments.
    If you are unable to load any pages, check your computer's network connection.
    If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web."

Mean anything to you??

I have no problems accessing ANY other site that I choose to visit...JUST Epson's.

Beyond the basics, I confess that networking and the worldwide web are mostly a mystery to me; when they play up, I am LOST.

Mike.

---

### Post by Mike_Walsh on 2014-06-24
Hi, sammiev.

I'm glad to hear that you (and no doubt, everybody else) can all access Epson's site with no problems; good for you!

For some obscure, yet no doubt very simple reason, I CAN'T; amazing, isn't it?

I've been messing about with these things for well over 30 years now.....and they STILL catch me out, with no problems AT all. *Sheeeesh...*

Mike.

---

