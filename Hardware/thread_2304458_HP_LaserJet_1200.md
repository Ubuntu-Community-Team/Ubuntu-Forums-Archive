---
title: "HP LaserJet 1200"
date: 2015-11-26
forum: Hardware
---

### Post by richramik on 2015-11-26
Have an issue with the HP LJ 1200.  Running 14.04; HP 1200 connected with a USB; using hilip; HP Pavilion 500 PC.  

The issue is speed, or rather the complete lack thereof.  This is especially true for a document containing any type of graphics.  As for a PDF, I can and have waited for up to an hour or more to print a page.  As I am typing this, I am trying to print my itinerary/airline ticket confirmation.  It has already been 35 minutes and still nothing has printed.  I came from Windows XP shortly after 14.04 was released, and never experienced anything like this.  It there any remedy for this complete lack of speed?

Also, looking for a recommendation for a color laser printer that will actually work.

Lastly, I'm not a techy type, so would appreciate any replies in simple to understand language.

Thanks,
Rich Ramik

---

### Post by tgalati4 on 2015-11-27
Look for errors in /var/log/cups.  Open a terminal:

```
more /var/log/cups/errors_log
```

Spacebar to page forward.  "q" to quit.

I have a 1200 hung off of a 12.04 server and never had any problems with it.  True, there are some pathological PDF's out there--like maps and some published brochures put out by governments, like train schedules and the like--things you would like to print out, but are so heavily-formatted, that fail to print correctly.  Can you view the documents in *xpdf* or *evince*?  Do they look formatted correctly?

Can you dual-boot into WinXP and print the document and time it?  It the document does not contain any personal information, perhaps post it.  I have a collection of pathological PDF's.  I collect them.  It's a hobby of mine.

---

### Post by Cbhihe on 2015-11-27
I am not giving you a solution but rather describes what it takes to find one... and I have no doubt that if you keep at it you **can** find a satisfactory solution, without having to just throw money at it...
Printer related issues are usually time-consuming to troubleshoot, in particular when you start from scratch. 

I print from 14.04 on an HP Laserjet 4P (yes, from a 20 yr old 4P !!) flawlessly. Thank you HP for not having programmed obsolescence in that case ! The upshot was that I had to spend literally 3 or 4 full days (I blissfully forgot exactly how long) to understand the printer's interface, what *HPLIP* can do for you, finding an appropriate driver and finally resorting to installing *CUPS* ([http://www.cups.org/](http://www.cups.org/)) to be able to manage yr print queue and more from a nice web interface, using yr favorite browser. 

As a side note, slowness may just arise with inadequate drivers, **even** if the driver that you use is identified as the driver for your printing hardware. HP offers boatloads of drivers ([https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)) and I would at one point recommend that you also try drivers, whose names do not feature your exact printer name.  Rather try a drivers name close to your printer's name. For instance try the driver for HP LJ 950 (if it exists) or LJ 1000 or LJ 1300. The preceding models names are provided purely as examples, not because they exist. They might not exists. (In any case I have not checked.)  This is what I did and now my printer functions both from USB as well as from my home network ([https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)), when I hook my printer up on my main router.  

In any case, I do second @tgagalati4's suggestion: boot from WinXP and try to print your pdf file on the same printer. This should be your baseline for benchmarking. If it does print normally and at a reasonable speed, then you can bet that you will also be able to do so from Ubuntu.

Good luck.

-ced

---

