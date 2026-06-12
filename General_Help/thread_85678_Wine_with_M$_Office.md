---
title: "Wine with M$ Office?"
date: 2005-11-03
forum: General Help
---

### Post by Mr. Electric Wizard on 2005-11-03
Has anyone gotten M$ Office 2000 to install with Wine?
This is basically the only thing holding back from Diving into Linux fully.
I installed Wine several months back, before Wine entered Beta Stage and I could not get it to work.
When I ran the setup.exe I kept getting an error.

Just wondering what I should do to troubleshoot this?

---

### Post by Mr. Electric Wizard on 2005-11-03
Nevermind guys, I did some more checking around and it looks like it just ain't he time to try this yet...
Looks like wine has to cure a little longer before it'll be ready, and I really don't want to pay for Crossover Office either.
Oh well.
:cool:

---

### Post by pickarooney on 2005-11-03
And OpenOffice 2 just doesn't cut it?
You probably need all the macros and stuff, right?

---

### Post by jonny on 2005-11-03
Wine can be made to work with Office 2000.  I got much further than you, but gave up before it was working properly and I learned to love OO2 instead.  My unfinished work related to printing and Word mysteriously switching my left and right mouse buttons.

You need to know a few tricks, but I can only remember the broad strategy, not the details.  First, you need to ensure you can see hidden files on your CD drive.  That means you have to fiddle with /etc/fstab.  Next, you have to make sure that you have a good version of Wine.  Some alpha builds broke MS Office.  Third, make sure that you use the Wine config tool to install all the prerequisites for installation (eg internet explorer – I hope you have a licence!).  Finally, don’t try to install by using the CD directly – it fails.  Use Wine’s own Office installation program instead.

Alternatively, shell out $40 and get Crossover Office.  I trialled it and it worked perfectly for me – I just didn’t like MS Office enough to bother keeping it.

One final ironic twist: I have one particularly large spreadsheet that is opened easily on my laptop by OO2 or Excel under Wine, but which causes a complete machine crash and reboot if I open it under Windows.  Excel is notorious for having bad memory management.

---

### Post by Mr. Electric Wizard on 2005-11-03
Basically it boils down to me being lazy...
Here's the scenario.  I am a Professional Real Estate Inpspector and my Template for the report that I have to write is in Word format.
When I open this document with OOo, the formatting is not even close to being right.  In addition, there are Checkboxes that I must be able to check and uncheck.  So far I have not been able to get any of the FOSS word processing programs to show the formatting correctly.

I could reformat the document to make it look like the Word 2000 version, but that would be a major PITA.  I have also tried AbiWord, and a few other programs...

---

