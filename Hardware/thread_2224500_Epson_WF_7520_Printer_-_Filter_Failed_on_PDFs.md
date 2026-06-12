---
title: "Epson WF 7520 Printer - Filter Failed on PDFs"
date: 2014-05-16
forum: Hardware
---

### Post by lile001 on 2014-05-16
Got a shiny new Epson WF-7520 printer.  Yay! 
Some things will not print.  

Will not print from PDF
Will print OK from Chrome
Will print OK from Libreoffice
Will print OK from Gedit
Will scan OK from simplescan
Test page from [COLOR=#333333][FONT=Ubuntu Beta]"System" -> "Administration" -> "Printers" prints OK[/FONT][/COLOR]

On the jobs that won't print (PDFs are the only ones I have run across so far) CUPS (localhost/631) reports stopped "Filter Failed". 

So far my googling on this error has run me down several ratholes but not found the solution to it.  So, yes, I have RTFM'd but perhaps did not grok it.  

Here is what I have tried:

1.  Downloaded these files and installed them:

 iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb
 iscan-data_1.28.0-2_all.deb
 iscan-network-nt_1.1.1-1_amd64.deb
 iscan_2.29.3-1~usb0.1.ltdl3_amd64.deb
 epson-inkjet-printer-201115w_1.0.0-1lsb3.2_amd64.deb

2. Installed new printer via Cups and picked the Epson WF 7520 driver from the list provided.  Tested a scan and it worked OK, printed a test page from the printer front panel menu.  PDFs fail to print. 

3. Deleted and reinstalled said printer using the list provided

4. Find a PPD file in /opt/epson-inkjet-printer-201115w/ppds/Epson.  Extract it (as root) to that folder.  Copy it to /opt/epson-inkjet-printer-201115w/cups/lib/filter.  Sudo chmod 775 on both those files.  
(Don't ask me why I thought of this, I was following a thread in which this worked for somebody. If these were dumb things to do, feel free to jeer or throw vegetables.) 

 5. Sudo chmod 775 /opt/epson-inkjet-printer-201115w/cups/lib/filter/epson_inkjet_printer_filter  which apparently worked for a guy in another thread on the subject. 

6. Made sure I am in the right group (I always love being in the right group!)  
```
$ cat /etc/cups/cupsd.conf | grep SystemGroup
SystemGroup lpadmin

$  cat /etc/group | grep -i lawrence

lpadmin:x:109:lawrence




```

7. I am having some trouble attaching /var/log/cups/error_log, I will try again in a comment or just copy the whole thing in there. 

8. as indicated in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1080187"):  I tried:
```

[COLOR=#333333][FONT=monospace]sudo chmod o+rx /var/spool/[/FONT][/COLOR]
sudo service cups restart

```

9. Delete and reinstall the printer in cups, choosing the above-mentioned PPD. 

10. Dleete and reinstall the printer in cups, using the printer driver provided in the dropdown list. 

Fun, new stuff added in an edit:

11.  Plug in the printer to USB and install via cups as a local USB printer.  No joy here. 

12.  Found this obscure line in /var/log/cups/error_log:
I [16/May/2014:13:08:22 -0500] Please move "SystemGroup lpadmin" on line 3 of /etc/cups/cupsd.conf to the /etc/cups/cups-files.conf file; this will become an error in a future release.

Deleted this line from cupsd.conf and found it already appeared in cups-files.conf




Well, suggestions as to what to try next are appreciated.

---

### Post by lile001 on 2014-05-16
Error log is 2.9 MB.  Can't upload.  If this file is important, perhaps you could ask about a particular section of it.  

Here is a snippet:

E [16/May/2014:12:55:29 -0500] [Job 672] Job stopped due to filter errors; please consult the error_log file for details.
D [16/May/2014:12:55:29 -0500] [Job 672] The following messages were recorded from 12:55:28 to 12:55:29
D [16/May/2014:12:55:29 -0500] [Job 672] End of messages
D [16/May/2014:12:55:29 -0500] [Job 672] printer-state=3(idle)
D [16/May/2014:12:55:29 -0500] [Job 672] printer-state-message="Data file sent successfully."
D [16/May/2014:12:55:29 -0500] [Job 672] printer-state-reasons=none
W [16/May/2014:13:01:25 -0500] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_WF-7520_Series-Gray..' already exists
W [16/May/2014:13:01:25 -0500] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_WF-7520_Series-RGB..' already exists
W [16/May/2014:13:01:27 -0500] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_WF-7520_Series-Gray..' already exists
W [16/May/2014:13:01:27 -0500] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_WF-7520_Series-RGB..' already exists
E [16/May/2014:13:01:40 -0500] [Job 673] Job stopped due to filter errors; please consult the error_log file for details.
E [16/May/2014:13:06:40 -0500] [Job 673] Stopping unresponsive job.
I [16/May/2014:13:08:22 -0500] Please move "SystemGroup lpadmin" on line 3 of /etc/cups/cupsd.conf to the /etc/cups/cups-files.conf file; this will become an error in a future release.

---

### Post by lile001 on 2014-05-16
Well Well - I got a PDF to print from Okular, but not from Document Viewer!  Stand by for more testing, we may have a solution.  Hope this helps someone.

Able to print 8-12X11 from top tray.  Attempts to print 11X17 come out of the botttom tray. But they are still 8.5X11 printed area.    

However, futzing around with paper sizes and bottom tray generated a "Filter failed" message in Okular!  OK, we are onto something here - maybe the filter failed message is all about paper sizes?  More testing ...

Am able to print OK from okular with default 8.5 X 11 paper sizes from either tray, on either 8.5 X 11 or 11X17 paper.  So far unable to get prints to fit 11X17, can't find the correct paper size that matches that.  

Printer front panel controls:  Paper size notice was off.  Turned paper size notice on.  AHA!  Trying to print an 11X17 generates a lot of beeping and a paper size error.  I set up custom paper size in Cups to be 11 wide by 17 long and the printer choked on it. Also started spewing out blank sheets.  OK we are onto some clues here, no joy yet.

Deleted USB printer in Cups, reinstalled network printer, accept defaults and able to print 8.5X 11 in the top tray on 8.5X11 paper.

11X17 = 279.4 X 431.8 mm. There are no papersizes in the default cups list that match this size (!)

Trying to print an 11X17 in Libreoffice generated the same "filter failed" error.  This is definitely related to the fact there is no available 11X17 paper size in the cups driver for this printer.  Custom paper sizes also generate this error. 

Tried using some other epson printer drivers (nope), telling the printer front panel menu that it had A3 in the second tray and then printing to A3 (nope) 

A long struggle with making a custom ppd file [per this thread]("http://stackoverflow.com/questions/1028891/whats-the-easiest-way-to-add-custom-page-sizes-to-a-ppd") has so far not produced anything.  If anyone wants a good laugh I can post the hacked PPD file I created.  Seems like I tried this before without much success.  There is actually a utility for checking ppd files, so I am pretty sure I made a valid one.  I can get an option for Tabloid to show up in the print dialogue, but haven't been able to actually make it print without throwing errors.  

I can tell you categorically that Epson WF7520's DO NOT print 11X17's under Linux's Cups system out-of-the-box. 

If this printer won't print 11X17s it is going back in the box!

---

### Post by pqwoerituytrueiwoq on 2014-05-16
Is the pdf you want to print formated to 11x17?
document viewer File -> Properties -> General Tab -> last row

IMO if you want out of the box printer support go for HP printers, i have only set up 1 epson printer and it was easy to get the driver, never had to even open a web browser the system offered it to me from the add printer setting section, more than i can say for canon printers

---

### Post by lile001 on 2014-05-16
Thanks,  pqwoerituytrueiwoq

Yeah, the printer chokes when I send it anything set as 11x17, and does not have any available paper sizes 11x17.  My attempts at hacking it to accept 11x17 have just wasted a day of precious time.  

I've had fair luck with HP printers too, but more trouble with the latest HP wide format printer.  I went with Epson based on rave reviews online.  This printer is going back int he box, maybe I'll go back to HP.  Too bad, their quality has waned recently.  Should be about $50 cheaper though.

Can't attache the hacked ppd file due to file size restrictions.    I'm pretty proud of this hack, except for the fact it didn't work (sarcasm)   Contact me if you want a copy to play with.

---

### Post by pqwoerituytrueiwoq on 2014-05-16
well good luck
the only dumb question is the one you don't ask
Off topic:
BTW monkeybrain20122's advice in that [other thread]("http://ubuntuforums.org/showthread.php?t=2224297&page=2") you have is good advice, put a sign in your window 'looking for skilled linux tech', i would jump on that like mosquitoes attack me when i step outside if i were to see that

---

### Post by lile001 on 2014-05-16
Well, finding another [source of information here]("http://www.openprinting.org/printer/Epson/Epson-WF-7520") that claims to have printer drivers for this printer.  Following up, will report soon.

Nah, same noise, no option to print 11X17 or tabloid, chokes if you try.  Some other guy named Benoit also left a message there with the same beef.


Hopefully my blogging this problem by myself in this thread will result in someone else finding it later and benefitting, pretty much only me and the crickets in this little corner of Ubuntu-land. I do this as much to leave some breadcrumbs for some other poor schmoe with the same problem as anything else. I have found about twenty posts in various linux forums about Epson printer "filter failed" bugs and no solution there. 


I may have a solution! I'll state this really plainly so that even I could google this answer:


Epson Printers (many of them) choke on certain paper sizes under Linux Cups print system and Epson Drivers. They throw messages like "Filter failure". The problem seems to stem from the drivers provided by Epson (which are "unsupported") not allowing valid paper sizes such as Tabloid. These printers work fine under Windows. 


The solution I've hit on leverages this fact. Sit an old Windows box in the corner, set up the printer on the windows, and print through Linux via Samba. I thought of this last night late, haven't tried it yet. I'll post here if the solution works. My wife is about sick of Ubuntu for no apparent reason, she'll be pleased.

/Edit
Well,  no such luck.  It still looks like Cups still tries to use Epson's Linux driver to talk to the printer, even if it is sitting on a Windows machine and even if it is connected through Samba.  

The best hack (and this is no hack at all) is to sit the windows box in the corner, connect the Epson printer to it, and any paper size that isn't 8.5 inches wide has to be printed sitting at the Windows box.  Well, it is still a really awesome printer even if Epson's drivers stink.

---

### Post by lile001 on 2014-05-17
Well, not too much interest in this problem apparently. Just me and the crickets here.  Just for grins I am posting the ppd file hack, at least a shortened version of it. From what little I know of these things this *should* work.  However if there is anything inconsistent in the information sent to the printer, like pageregion doesn't match pagesize, the print fails on "filter failed".  I don't know where this message comes from - Cups or something else?

/edit
Epson comes with a "filter" program that is called by the PPD file.  I think this program located at /opt/epson-inkjet-printer-201115w/cups/lib/filter/epson_inkjet_printer_filter is the heart of the problem.  This line of the PPD

*cupsFilter:    "application/vnd.cups-raster 0 /opt/epson-inkjet-printer-201115w/cups/lib/filter/epson_inkjet_printer_filter"

points to it.

---

