---
title: "Epson WF-3620"
date: 2014-08-11
forum: Hardware
---

### Post by loutchoa on 2014-08-11
Dear Ubuntu Forum,

I have just installed a brand new Epson WF-3620 printer. Seems to work like a charm when I send documents from Windows, but has very low printing quality from mu Ubuntu 12.04. The drivers are the one provided from Epson website. Anybody with a similar experience, and a solution?

Cheers
François

---

### Post by grier-devon on 2014-08-11
set it up with CUPS, CUPS should provide the drivers in setup and if it is wireless it should auto detect the printer. Did with my Hp.

Official documentation from Ubuntu
[https://help.ubuntu.com/10.04/serverguide/cups.html](https://help.ubuntu.com/10.04/serverguide/cups.html)

---

### Post by pdc on 2014-08-12
these WF series of printers (WorkForce) seem to come with generic drivers from Epson: not the full feature linux driver they provide with home printers; (they have had a good reputation for their home printer support for linux);

if one can source a ppd file from the drivers provided for windows then that might be the best option

curious to what extent printing capability is built into device eg [http://www.epson.com.au/products/multifunctional/WorkForce_WF-3620.asp?groupid=3](http://www.epson.com.au/products/multifunctional/WorkForce_WF-3620.asp?groupid=3)

> Print from your iPad or iPhone

Apple® AirPrint™ makes it simple to print emails, photos, web pages and documents straight from your iPad or iPhone. There's no software to download, no drivers to install and no cables to connect. Your Apple device will automatically connect to the printer.


---

### Post by loutchoa on 2014-08-19
I tried, but drivers proposed by CUPS don't work. I need to use the drivers provided by Epson, I guess....

---

### Post by loutchoa on 2014-08-19
Would you have any idea how to extract ppds from Windows drivers, this would be great, and not only in my case....
Or have I to use the windows machine or wait for a new version of linux drivers :-(


/F

---

### Post by JeQhdMD on 2014-09-01
Loutchoa, 

Have you tried the Workforce printer drivers from the Ubuntu Software Center ???. . the series is listed under WF3520,3530 and 3540.   I would give this driver package a try - - I had one Epson printer a few years back that I used this method for, and the printer worked fine.  By the way, I have two Workforce printers . . . the WF 645 and the WF 2540.   All functions work well (scanning, copy, fax and print.)   The print quality is excellent.   There are a lot of options for print settings (which are accessed via "properties"  - - see System Settings>Printers>Epson WF-3520 series . . ).  This allows you to control the quality of print and many other options.

After doing that, set it up for Cloud Print (from Google) and you'll have more options.   Just note the IP address (from your Printer setup menu) and type the IP into your browser to access the Cloud Print Control Panel.

Hope this helps.

PS:   here's a good resource I use often:   [http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/databaseintro](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/databaseintro)

---

### Post by christopher9 on 2014-09-03
"the series is listed under WF3520,3530 and 3540" 

I'm not finding anything for Epson printers in Software Center using that....do you have more information ?

---

### Post by JeQhdMD on 2014-09-06
Yes.  Here's what needs to be done in order for the drivers to show up in the Ubuntu Software Center:  you have to update your software "sources" (System Settings>Software & Updates>Other Software tab> . . . add:   [http://download/ebz.epson.net/dsc/op/stable/debian/lsb3.2](http://download/ebz.epson.net/dsc/op/stable/debian/lsb3.2) main.  Input your password when prompted, and then update the software cache (reload).

Another way to get the drivers is by going to . . . [http://www.openprinting.org/printers](http://www.openprinting.org/printers) . . . then use the search tool and specify Epson and highlight the 3520 series.   The 3620 is not yet specifically listed (maybe too new), but I would try to install the driver listed for the 3520 series (i.e., "1.0.0 DEB for LSB 3.2).

If that driver doesn't work, you may need to contact the Open Printing Epson team (via Linux Foundation) and see when the newest driver will be ready for release.

---

### Post by dcabernel on 2014-10-23
Exact same issue. With Epson driver; prints but low quality from Ubuntu 12.04. Prints fine from Win8 (or Android phone). CUPS 3540 drivers didn't print, just spit out blank page after blank page.

Any resolution?

> **loutchoa said:**
> Dear Ubuntu Forum,

I have just installed a brand new Epson WF-3620 printer. Seems to work like a charm when I send documents from Windows, but has very low printing quality from mu Ubuntu 12.04. The drivers are the one provided from Epson website. Anybody with a similar experience, and a solution?

Cheers
François

---

### Post by nuruddin-1 on 2014-10-25
Hi
I am having the same issue on 14.04 any solutions??  I'm thinking of returning this great printer

---

### Post by dcabernel on 2014-10-26
I printed through Google Cloud Print and it worked fine; although it's a bit of a pain to upload and print from there. I believe I'd be more inclined to transfer the file to my Win8 Laptop and print from there controlling the Laptop remotely. I usually have it on and connected in my office anyway.

---

### Post by sammiev on 2014-10-26
Goto the Epson driver [site]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") and enter 3620 in the search box and download the deb file required.

---

### Post by dcabernel on 2014-10-27
This is the driver I am using that prints looking washed out. "Epson WF-3640 Series - epson-inkjet-printer-escpr 1.4.3-1lsb3.2 (Seiko Epson Corporation LSB 3.2) (color, 2-sided printing)"

Printer is WF-3640 not 3620 but's its the same driver anyway.

---

### Post by Mike_Walsh on 2014-10-28
> **loutchoa said:**
> Dear Ubuntu Forum,

I have just installed a brand new Epson WF-3620 printer. Seems to work like a charm when I send documents from Windows, but has very low printing quality from mu Ubuntu 12.04. The drivers are the one provided from Epson website. Anybody with a similar experience, and a solution?

Cheers
François

Hallo, Francois.

This might seem like a silly question, but.....

In the Epson Download Center; at the bottom of the download page with the driver listings, did you miss the small foot-note? The one that says you must

```
sudo apt-get install lsb
```

first.....BEFORE installing the printer driver?

People often overlook these small footnotes on Epson's download pages. Just a thought.

I have an SX218. The driver you've used is supposed to work with my printer as well, but it tends to print garbage with that one, so I installed the specific 'full-feature' driver for mine. With Epson, they appear to offer one 'generic' Linux driver for the whole range, as well as specific 'full-feature' drivers for certain groups within the range. Having researched it, it appears that for the generic driver, you MUST install the lsb package first. I didn't know that myself until just now; it's probably why the 'generic' driver didn't work with mine, and why I ended up using the 'full-feature' one, which does.

Unfortunately, there doesn't appear to be 'full-feature' driver specifically for your printer; as JeQhdMD noted in post #8, it could be that your printer is too new. The problem is that Avasys (a Japanese software company) who originally developed the Epson range of Linux printer drivers, quit doing so back in September 2012, and handed the repos over to Epson themselves.....since which time, very little or no development work has been done for Linux.


Regards,

Mike. ;)

---

### Post by stevedude on 2014-10-28
Try [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

This is the preceding page that also includes Epson's Links to all things Linux: [http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=232591&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX](http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=232591&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX)

---

### Post by alex285 on 2014-11-06
> **loutchoa said:**
> Dear Ubuntu Forum,

I have just installed a brand new Epson WF-3620 printer. Seems to work like a charm when I send documents from Windows, but has very low printing quality from mu Ubuntu 12.04. The drivers are the one provided from Epson website. Anybody with a similar experience, and a solution?

Cheers
François


Hi,
I dont know what you mean by "low printing quality", but my problem was that the printing resolution was very low. The blacks looked grey and the colors were very weak. I thought it was a driver issue and updated to the latest  (epson-inkjet-printer-escpr-1.4.4-1lsb3.2), but the issue remained. In the end the solution was simple:
In "Printer Properties"->"Printer Options" you need to select under "Quality": NormalPaper-Standard-Vivid. I guess  the "Normalpaper-standard" setting just has a low resolution. Now all prints look fine.

Hope this helps

---

### Post by dcabernel on 2014-11-06
> **alex285 said:**
> Hi,
I dont know what you mean by "low printing quality", but my problem was that the printing resolution was very low. The blacks looked grey and the colors were very weak. I thought it was a driver issue and updated to the latest  (epson-inkjet-printer-escpr-1.4.4-1lsb3.2), but the issue remained. In the end the solution was simple:
In "Printer Properties"->"Printer Options" you need to select under "Quality": NormalPaper-Standard-Vivid. I guess  the "Normalpaper-standard" setting just has a low resolution. Now all prints look fine.

Hope this helps

Doh!! :p

 Too simple. I thought I checked options and there was nothing like that. Must have been a different driver i was using at the time. Looks great, test print is VIVID!

 Thanks.

---

### Post by gargame on 2015-02-06
Hi,

thank you so much alex285 !!! 
Your "Printer Properties"->"Printer Options" you need to select under "Quality": NormalPaper-Standard-Vivid in place of "Normalpaper-standard" saved this bad quality printing problem for me too on an EPSON WF-4640 !

Thank you, 

Regards,

---

### Post by loutchoa on 2015-02-08
After having almost given up,  [http://www.openprinting.org/printers](http://www.openprinting.org/printers) suggested to set the paper type to "plain papers-High. It fixes the problem for me, though seems to print a bit slowly.

Cheers
François

---

### Post by hamcatcher on 2015-02-22
Hi has anyone been able to "make a full featured driver" ie from say the 3520 ppd or so?
When I have tried to use the 3520 it only spits out empty pages, but perhaps the differences are small ?

thanks

---

### Post by pdc on 2015-02-24
someone could well be trying to make a "full-featured" driver for the WF-3520

..........but you could just go to the Epson site and type in "WF-3520" and it takes you here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71)

......... Epson appear to offer a full featured driver for the WF-3520 ......................

and they provide [COLOR="#008000"]epson-inkjet-printer-201212w_1.0.0-1lsb3.2_i386.deb[/COLOR] or [COLOR="#008000"]epson-inkjet-printer-201212w_1.0.0-1lsb3.2_amd64.deb[/COLOR]

---

### Post by tahnik-mstsn on 2015-04-04
> **alex285 said:**
> Hi,
I dont know what you mean by "low printing quality", but my problem was that the printing resolution was very low. The blacks looked grey and the colors were very weak. I thought it was a driver issue and updated to the latest  (epson-inkjet-printer-escpr-1.4.4-1lsb3.2), but the issue remained. In the end the solution was simple:
In "Printer Properties"->"Printer Options" you need to select under "Quality": NormalPaper-Standard-Vivid. I guess  the "Normalpaper-standard" setting just has a low resolution. Now all prints look fine.

Hope this helps

Sir, I just registered to say thank you very much. You saved a lot hassle Sir.

Thank you again

---

