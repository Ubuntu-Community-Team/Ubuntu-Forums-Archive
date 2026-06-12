---
title: "Xubuntu v. Epson"
date: 2014-01-26
forum: Hardware
---

### Post by manikinxvx on 2014-01-26
I am working to get my Epson Expression XP-310 Small-in-One&#8482; [ [http://www.epson.com/cgi-bin/Store/jsp/Product.do?sku=C11CC88201&BV_UseBVCookie=yes](http://www.epson.com/cgi-bin/Store/jsp/Product.do?sku=C11CC88201&BV_UseBVCookie=yes) ] to work with my Dell Optiplex 755 running Xubuntu 12.04.4, Precise Pangolin. So far, depite installing all software references to drivers for this printer, I have only made progress, yet even this remains untested, using the complete Gutenprint package [ [http://sourceforge.net/projects/gimp-print/?source=dlp](http://sourceforge.net/projects/gimp-print/?source=dlp) ]. Yet, despite the claims on the page it seems to only still work in GIMP, and since I don't use GIMP for *all* printing, I would like -- and *need* -- to be able to print from any and all applications. 

I had no issues at all, using the included software package, to get the wireless connectivity to work on our Windows7 machines, and as such I have found a temporary workaround by printing all files to PDF; putting them on GoogleDrive; and printing from another computer. Albeit, as I noted, this is merely a workaround and not at all a solution, in my mind.

One last notation on this matter. I did even try to install (as a last resort) the Windows package using Wine, but that failed; hung; and crashed upon attempt. So... no luck there, either.

Anyone have any thoughts/advice/ideas? Solutions?!

---

### Post by ajgreeny on 2014-01-26
Have you tried going to the web interface for CUPS which I found got my printer going even though using the system ->printing menu item failed.  My printer was an HP but I did not have an updated hplip which supported it, nevertheless CUPS managed easily, so it may do also for your Epson.

Point your web-browser to [http://localhost:631/](http://localhost:631/) if you haven't already done so and follow the prompts.

---

### Post by manikinxvx on 2014-01-26
The CUPS web interface seems to have done the trick for adding the printer to the options in the print menu. I'll test it momentarily and see if this issue is now resolved. Thank much, ajgreeny!

---

### Post by manikinxvx on 2014-01-26
Yes, that indeed did work. Again, ajgreeny, thank you for that advice. Now, I'm just wondering why my hours of research on this matter yielded absolutely no results related to CUPS. That information popping up in Google sure would have save me loads of irritation. 

Until only a few months ago, my experience with Linux was only as an end-user. Now that I'm running it at home, as both user and admin, I'm learning a lot... but still have much knowledge to acquire.

---

### Post by ajgreeny on 2014-01-26
I know that feeling!

I was not aware of the CUPS web interface for a long time either, but now it is bookmarked in my web-browser just in case I have problems.

I am very pleased you have your problem solved, and welcome to this great forum;  I learned almost all I know of Ubuntu from being a member since 2005 when I first started using Ubuntu 5.04.

---

### Post by manikinxvx on 2014-03-01
I never did follow up on this issue. Apparently, the issue is not resolved. 

CUPS reads that the printer is ready and accepting jobs on one page ([http://localhost:631/printers/](http://localhost:631/printers/)), but then on another page ([http://localhost:631/admin/](http://localhost:631/admin/)) it reads, "No printers found." Is there anyway/anywhere I might be able to manually enter the printer's IP address and see if that resolves things for a successful connection to the printer that includes a completion of print jobs and actually generates output?

---

### Post by sammiev on 2014-03-01
> **manikinxvx said:**
> I never did follow up on this issue. Apparently, the issue is not resolved. 

CUPS reads that the printer is ready and accepting jobs on one page ([http://localhost:631/printers/](http://localhost:631/printers/)), but then on another page ([http://localhost:631/admin/](http://localhost:631/admin/)) it reads, "No printers found." Is there anyway/anywhere I might be able to manually enter the printer's IP address and see if that resolves things for a successful connection to the printer that includes a completion of print jobs and actually generates output?

This is what I use for [Epson]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") all-in-one printers. Just enter in XP-310 in the search box and Linux in operation box.

---

### Post by manikinxvx on 2014-03-01
> **sammiev said:**
> This is what I use for [Epson]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") all-in-one printers. Just enter in XP-310 in the search box and Linux in operation box.

Search box & Operation box... where... ?

---

### Post by sammiev on 2014-03-01
> **manikinxvx said:**
> Search box & Operation box... where... ?

Click on the word [Epson]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX").

---

### Post by manikinxvx on 2014-03-04
Yes... I've downloaded and installed all software available for Linux as it pertains to the XP-310. The issue simply (albeit complex in itself) is that everything tells me that the printer is ready and present... except for when I actually print. Then, the printer is unresponsive the displayed message flashes from printing to not connected. Terminal tells me that the printer has been ready to run since initial set-up date.

---

### Post by sammiev on 2014-03-05
> **manikinxvx said:**
> Yes... I've downloaded and installed all software available for Linux as it pertains to the XP-310. The issue simply (albeit complex in itself) is that everything tells me that the printer is ready and present... except for when I actually print. Then, the printer is unresponsive the displayed message flashes from printing to not connected. Terminal tells me that the printer has been ready to run since initial set-up date.

Make sure you delete the first one you installed and or choose the new one added.

---

### Post by manikinxvx on 2014-04-08
Upon upgrading to Raring Ringtail and jumping through only a couple of flaming hoops, this issue has become null and void. The printer is working quite well with this version of Xubuntu. 0_o

---

