---
title: "Recent cups upgrade? Printing problems"
date: 2009-06-16
forum: Hardware
---

### Post by eudemus on 2009-06-16
Has there been a recent cups upgrade? My printing has suddenly failed, for no obvious reason.

I run Kubuntu Hardy, CUPS, Foomatic drivers and print via a printer attached to a Belkin Router/USB Print Server, which has been working fine for the last several months.

I have tried reinstalling all the bits of cups that I can think of, reinstalling printers, and so on. I occasionally get something to print (but invariably not from any pdf programme - which is what I actually need right now).

acroread actually crashes if you try to print.

What IS happening? Happy to post logs if someone can help me find the relevant ones.

Cheers for any assistance.
Eudemus

---

### Post by Hintzy64 on 2009-07-20
I'm having a similar/same problem in Ubuntu Jaunty.  My printers worked fine until a few weeks ago.  But now when I send a print job, the printer warms up, I get a notification that the job printed successfully, but nothing ever prints.  I've tried multiple printers in my office (all network printers via TCP/IP), Ricoh, Savin, HP, all give the same result.  I have WinXP running in VirtualBox and can print fine from there, so it's not a network connectivity issue.

Looking at my package history in synaptic, it appears that this started when I upgraded from CUPS 1.3.9-17ubuntu3.1 to 1.3.9-17ubuntu3.2.  I'm not sure if this is exactly when it broke, there could have been another upgrade around the same time that did it.  I tried forcing a downgrade to 1.3.9-17ubuntu3.1 this morning, but synaptic wanted to remove the LSB and ubuntu-desktop packages, and returned an error when I wouldn't permit those changes.

I've also tried reinstalling cups/printing packages and the printer drivers, but no luck.  As above, I can post logs if you tell me which ones to look for! :-)

Thanks,
-John

---

### Post by Hintzy64 on 2009-08-21
This is still a problem for me, no printing since the June 29 CUPS upgrade.  The printer warms up, but does not print.  The system tray notification reports that the printing job is complete.

Anybody figured a way around this?  Any info I can provide to help figure it out?  It looks like CUPS 1.3.10 is available in Karmic, do I just have to wait for that and hope it works?  :(

Thanks,
-John


> **Hintzy64 said:**
> I'm having a similar/same problem in Ubuntu Jaunty.  My printers worked fine until a few weeks ago.  But now when I send a print job, the printer warms up, I get a notification that the job printed successfully, but nothing ever prints.  I've tried multiple printers in my office (all network printers via TCP/IP), Ricoh, Savin, HP, all give the same result.  I have WinXP running in VirtualBox and can print fine from there, so it's not a network connectivity issue.

Looking at my package history in synaptic, it appears that this started when I upgraded from CUPS 1.3.9-17ubuntu3.1 to 1.3.9-17ubuntu3.2.  I'm not sure if this is exactly when it broke, there could have been another upgrade around the same time that did it.  I tried forcing a downgrade to 1.3.9-17ubuntu3.1 this morning, but synaptic wanted to remove the LSB and ubuntu-desktop packages, and returned an error when I wouldn't permit those changes.

I've also tried reinstalling cups/printing packages and the printer drivers, but no luck.  As above, I can post logs if you tell me which ones to look for! :-)

Thanks,
-John

---

