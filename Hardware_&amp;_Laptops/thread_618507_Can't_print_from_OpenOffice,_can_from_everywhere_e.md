---
title: "Can't print from OpenOffice, can from everywhere else"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by haydentech on 2007-11-20
I've seen various other older threads about this, but no solutions posted.  I am running 7.10, upgraded from 7.04.  The printer in question is an HP 4000N connected via Ethernet.  The test page prints fine, and I can print from Firefox and any number of other applications, but NOT from OpenOffice.

My printer is set up to use tray 2 and letter size paper by default.  My /etc/papersize shows "letter". If I select "Printer Settings" in OpenOffice, it shows that it will print to tray 2 in letter size.  So I hit print, and...

"Load tray 1 A4" on the printer, every time, and nothing prints.  There are no settings that show A4 or tray 1in any place that I can find, and in fact it shows just the opposite as I stated earlier.  This same behavior also happens with an HP Color LaserJet 4600, so it's not specific to that one printer.

It seems the somewhere, somehow OpenOffice really really wants to print A4 to tray 1 no matter what the printer setting say.  Help?

---

### Post by linuxonbute on 2007-11-20
> **haydentech said:**
> I've seen various other older threads about this, but no solutions 

It seems the somewhere, somehow OpenOffice really really wants to print A4 to tray 1 no matter what the printer setting say.  Help?

Try opening a document then select
File/print

when the 'Print' window opens click on 'Properties' and see what the paper is set to there.

---

### Post by haydentech on 2007-11-20
> **linuxonbute said:**
> Try opening a document then select
File/print

when the 'Print' window opens click on 'Properties' and see what the paper is set to there.

It shows Letter size and tray 2.

---

### Post by linuxonbute on 2007-11-20
Sorry I can't suggest anything then.

I need A4 here in U.K and had the problem that the default template that all my documents came from 
was set to a default of Letter.

I Hope someone else can help.

---

### Post by popch on 2007-11-23
Perhaps your documents are set to print on A4 paper? 

Check in OO under*** format/page settings*** or some such. I am guessing at the names of the menu entries as I don't use the English language version of OO.

---

### Post by linuxonbute on 2007-11-23
> **popch said:**
> Perhaps your documents are set to print on A4 paper? 

Check in OO under*** format/page settings*** or some such. I am guessing at the names of the menu entries as I don't use the English language version of OO.

That was the problem with my default template being set to letter when I wanted A4.

---

### Post by Lord Illidan on 2008-01-16
I had the same problem! Format -> Page settings worked, thanks!

---

