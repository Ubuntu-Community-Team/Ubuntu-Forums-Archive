---
title: "HP OfficeJet G55 ALMOST never prints!"
date: 2008-10-10
forum: Hardware
---

### Post by ladasky on 2008-10-10
Hi folks,

Printing seems to be my Number One Linux headache.

I have an HP OfficeJet G55 all-in-one printer/scanner/FAX, connected to a vintage 2003 Pentium 2.0 GHz CPU, via USB.  I have used it successfully as a local printer and as a network printer under Windows 2000, then Ubuntu 6, and finally Ubuntu 7.  I had some network printing problems when I switched over to Ubuntu, but the fine folks in this forum helped me to solve them.  I hope that you can help me out again!

After I upgraded to Ubuntu 8, things went awry.  Even local printing almost always fails to work.  The word *almost* is very important here.  I have an **intermittent** problem.  I have not determined how to reproduce the problem, OR how to reproduce correcting the problem.  It's driving me crazy.

Ubuntu 8 recommended the HP OfficeJet G55 Foomatic/hpijs driver.  That's the one I'm using.  There are four other drivers -- two more Foomatic drivers, and two CUPS drivers.  I'm not entirely sure how these differ.  BUT at times, using the recommended driver, I can print both locally and remotely.  I only remember CUPS being available under earlier revisions of Ubuntu, though I could be mistaken.

When I can print, I don't seem to have trouble with any specific application.  OpenOffice, Firefox, or Evince Document Viewer have all worked at one time or another.

For the sake of completeness, I will mention one idiosyncrasy of my USB setup.  As I mentioned, my machine is five years old.  I believe that it predates the USB 2.0 standard.  I have two USB ports.  One is dedicated to my mouse.  The other is swapped between the printer and my thumb drive.  Last year I tried to add a USB hub, with the idea of eliminating the plugging and unplugging.  My system would not recognize devices connected downstream of the hub.

In any case, I don't believe that this device-swapping has any effect on my printing problems.  Sometimes I unplug my thumb drive, plug in my printer, and it works.  Other times, it doesn't.

For now, I'm not trying to debug network printing.  If I can't get local printing to work, what's the point, eh?

When things are going wrong, the symptoms that I experience are as follows:

1)  A job goes into the print queue.  The printer executes its little startup routine right after I put the test page into the queue, where it moves the print head back and forth.  Then the print head makes a single pass across the page -- and hangs.  The status of the print job reads "processing."  If I give up after a while and push the cancel button on the printer, it ejects a page showing the top few lines of the requested job.  I have waited over an hour at times to see whether a print job will proceed.

2)  Sometimes when I look at the Ubuntu printer configuration panel, I find that the "enabled" check box has been unchecked.  I NEVER do this, the software is automatically unchecking this box for me.  When, I'm not sure.  Sometimes simply clicking the "enabled" check box is enough to get the printer to complete a stopped print job.  Other times, not.

3)  In an attempt to get things working again, I have tried clearing the print queue, shutting down both the computer and the printer, and rebooting.  Sometimes, to my great surprise, the print jobs I *deleted* from the queue will suddenly pop out of the printer after I restart!  Other times, not.

Even when things aren't working well, I can still print a test page directly from the Ubuntu printer configuration panel.  But it's SLOW.  The printer executes its startup routine.  Next, the print head makes ONE pass across the page -- and then goes quiet.  A minute or so later, the printer repeats the startup routine, and makes another single pass across the page.  And so on.  If I wait an hour, the full test page will be completed.  This is different than ordinary print jobs -- which, as I mentioned, can get stuck indefinitely after printing just one line.

I never use the FAX features of the OfficeJet, so I cannot say whether they work.  However: scanning works flawlessly.  

OK, where do I begin?  :confused:

---

### Post by Tamlynmac on 2008-10-11
I use the HPLIP driver for most all HP printers and your HP OfficeJet G55 is supported by this driver. I believe the newest HPLIP driver is version 2.8.9

[http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)

I used the auto installer and just follow the instructions. Solved many a problems with my HP printers.

---

### Post by ladasky on 2008-11-04
> **Tamlynmac said:**
> I use the HPLIP driver for most all HP printers and your HP OfficeJet G55 is supported by this driver. I believe the newest HPLIP driver is version 2.8.9

[http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)

I used the auto installer and just follow the instructions. Solved many a problems with my HP printers.

Hi Tamlynmac,
 
It took me a long time to try your suggestion, but it worked perfectly!  Thank you!
 
Thinking back, I believe that I did install HPLIP when I upgraded to Ubuntu 7.  I don't remember reading that it was required, in fact I don't remember the reason that I thought I should install it.  But when I upgraded to Ubuntu 8, of course I didn't have HPLIP any more.  The next time I upgrade the OS, I'll just have to remember to get HPLIP as well.
 
Where exactly does HPLIP reside in the printer data path?  Does it replace CUPS, or does it talk to CUPS?  Is there a reason that  HPLIP is not included in the Ubuntu distribution by default?  Just wondering...

---

### Post by Tamlynmac on 2008-11-04
That is an excellent question. I would think that the HPLIP driver would work inside the cups environment but am not certain. Hopefully, someone with more knowledge responds to this question.

Glad it work for you.

---

