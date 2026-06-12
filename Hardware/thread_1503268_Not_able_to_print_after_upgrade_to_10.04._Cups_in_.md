---
title: "Not able to print after upgrade to 10.04. Cups in a loop?"
date: 2010-06-06
forum: Hardware
---

### Post by jobrea on 2010-06-06
After a fresh installation of Ubuntu 10.04, the printer (Brother DCP-8045D, driver CUPS+Gutenprint v5.2.5 Simplified, connected to Lenovo X200 via USB) seems to be recognized, but doesn't print. However, sometimes after system restart it prints a test-page that I sent before restart.
The Document Print Status window says: Processing - Not connected?
cups-error-log in debug mode writes tons of similar lines (see attachment).
Is this a bug? Am I doing something wrong? Any help is appreciated!

---

### Post by parktownprawn on 2010-06-30
Not sure if it helps but I had a similar problem with my HP laserjet 1320. After upgrading to 10.04 it would give the message "Processing - Not connected?" even though the printer seemed to be initially recognised.

I deleted the printer using the Printing Dialog (System>Administration>Printing) and added it again.

When I added it again, I selected USB connection rather the HPLIP and now it seems to work fine. Maybe something similar would work for you.

---

### Post by ario on 2010-07-05
I tried.
But just shows me "Pending." Instead of "Processing - Not connected?".
It's not working:(
I want my printer back:((

---

### Post by ario on 2010-07-05
I tried.
It worked for me.
But only when I right clicked in **an empty area** of printers window and selected view print queue and deleted all prints in queue. Some of theme required me to restart my pc again and again and each time delete one of them from the queue. It was just like those crazy behavioral of windows. After deleting all queues printer statue was Online and ready to printing.
So it solved for me.

---

### Post by sdani on 2010-07-05
Thanks for your inputs, but it didn't work for me at all (probably because I am using kubuntu...).

But I found a solution, that works really fine for me.

I just opened the cups server ([http://localhost:631](http://localhost:631)) and added a new printer. After doing that, everything works perfectly now  :)

---

### Post by foresthill on 2010-07-09
I tried that but Firefox was unable to open the page. What gives?

EDIT: OK, I was able to finally get my HP Laser Jet 1320 to print. What I did was open printer properties, then go to "Device URI' and "change". At the bottom of the dialog box that opens, there is a "+" sign to the left of where it says "Connection". Click the plus sign and change the selection from "HP Linux Imaging and Printing" to "USB". That allowed the printer to work (for me anyway, YMMV).

One more thing I did to get PDF files to print was open them in Okular (you'll have to install this program, it does not come with the default install). Printing is glacially slow (probably 5 minutes for each page) but at least it works.

---

### Post by dino99 on 2010-07-09
on my end CUPS dont auto start on boot, so i need to start it into a console, then printing is ok

---

### Post by foresthill on 2010-07-09
So what's the command to start CUPS anyway? I tried "CUPS" and that did nothing.

I also tried:

 sudo /etc/init.d/cups restart

and got "command not found". 

Very frustrating. Do some people find this kind of thing fun? I sure don't.

---

### Post by grantbuntu on 2010-07-10
I am no expert but the following works for me (can't remember where I picked it up).

sudo service cups restart

You should then get the following:

* Restarting Common Unix Printing System: cupsd [OK]

---

### Post by foresthill on 2010-07-10
Thanks, I did get the command to work. Turns out I had a typo when I entered it in the terminal the first time. And I did get the confirmation message that CUPS had restarted. 

Unfortunately, it didn't make my printer work, I still got the "not connected" message when I would try to print.

---

### Post by johnfrith on 2010-07-20
For the record, I found that deleting and re-installing the printer (System > Administration > Printing) fixed the problem for me. Advise you to make a note of the URI (Printer > Properties) before you delete to save you having to track it down again, as I had to.

---

### Post by npatwari on 2010-07-28
> **foresthill said:**
> I tried that but Firefox was unable to open the page. What gives?

EDIT: OK, I was able to finally get my HP Laser Jet 1320 to print. What I did was open printer properties, then go to "Device URI' and "change". At the bottom of the dialog box that opens, there is a "+" sign to the left of where it says "Connection". Click the plus sign and change the selection from "HP Linux Imaging and Printing" to "USB". That allowed the printer to work (for me anyway, YMMV).

One more thing I did to get PDF files to print was open them in Okular (you'll have to install this program, it does not come with the default install). Printing is glacially slow (probably 5 minutes for each page) but at least it works.

This worked for me!  I tried everything on my HP Laser Jet 1320, which quit working after the 10.04 upgrade.  Thanks so much for this tip!

---

