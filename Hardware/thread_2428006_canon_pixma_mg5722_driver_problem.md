---
title: "canon pixma mg5722 driver problem"
date: 2019-09-28
forum: Hardware
---

### Post by jgw on 2019-09-28
I have a canon mg5722 printer.  Its been working just fine but, then, decided to only print the first page, if there are more than one page they are ignored.  I then took a look at my installation and searched the driver options available for the printer.  seems there are 2: 
canon mg5700 series - CUPS Guntenprint 5.2.13
canon mg5700 series - driverless, cups-filters 1.20.2

I have searched around trying to find which one to use but failed.  This printer is currently working wirelessly.

I also keep getting a notice that there is new firmware available.  I went to their site and they do not support linux nor are there any downloads.  It also says to install from settings/details.  Checked on that and it seems that notice for windows on (can be wrong on this one)

Thank you.........................

---

### Post by brian_p on 2019-09-29
[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting) could help. Both options should produce outputs of equal quality, but you could report on that. I would use the driverless option because it reduces the complexity of the printing chain and printer drivers will become unsupported in a future CUPS release.

I would be interested in what you get with ```
 avahi-browse -rt _ipp._tcp
``` and ```
 avahi-browse -rt _uscan._tcp
```

---

### Post by jgw on 2019-09-30
Thank you for the reply.  
avahi-brows stuff at: [https://pastebin.com/bdG1aDNh](https://pastebin.com/bdG1aDNh)

In settings this printer is: canon mg5700 series: driverless

I deleted this printer and re-installed it (easy way as it gives driver choices to install when installing)  It actually installed 2 printers, both the same: 
canon_5700_series
Does Not Accept Jobs

MG5700
Ready

The driverless driver is, evidently, automatically installed.  I also tried to goto ttps://wiki.debian.org/CUPSDriverlessPrinting but it was forbidden.  

I re-ran with the other driver: [https://pastebin.com/rPgChQRT](https://pastebin.com/rPgChQRT)

I then tried to print multiple pages again and, this time, it did it.  I also tried to do that with the driverless driver and it only printed the first page.  I also seem to have more printing options now.  
this has, so far, fixed the problem.

Thank you for the help!

---

### Post by brian_p on 2019-10-01
> **jgw said:**
> Thank you for the reply.  
avahi-brows stuff at: [https://pastebin.com/bdG1aDNh](https://pastebin.com/bdG1aDNh)

Thanks.

> In settings this printer is: canon mg5700 series: driverless

I deleted this printer and re-installed it (easy way as it gives driver choices to install when installing)  It actually installed 2 printers, both the same: 
canon_5700_series
Does Not Accept Jobs

MG5700
Ready

The driverless driver is, evidently, automatically installed.  I also tried to goto ttps://wiki.debian.org/CUPSDriverlessPrinting but it was forbidden.

This is sometimes an anti-spamming issue if a VPN is  involved. I think [email]wiki@debian.org[/email] is the address to contact for unblocking.

> I re-ran with the other driver: [https://pastebin.com/rPgChQRT](https://pastebin.com/rPgChQRT)

I then tried to print multiple pages again and, this time, it did it.  I also tried to do that with the driverless driver and it only printed the first page.  I also seem to have more printing options now.  
this has, so far, fixed the problem.

Thank you for the help!

My preference would be to get a URI with ```
driverless
```and use the command line with ```
lpadmin -p <printer_name> -v <URI> -m everywhere
```

---

### Post by jgw on 2019-10-03
Thanks for the help - Its running now so I will mark this as solved................

---

### Post by jgw on 2019-10-14
I thought I would add that I have trashed the printer.  It started to rip up the front of any paper being fed.  I tried to find a service manual that might help me take the printer apart but none were available.  I also talked to canon tech and was told that service manuals are not available to anybody.  So, I just gave up and trashed the printer <sigh>  I also explained that I couldn't understand why they wouldn't let owners have a service manual so they could mess with the printer that they had bought.  He just kept repeating that they did not have anything like that.  They do but, apparently, if you are not a qualified fixer of printers you are not allowed one <sigh>  The printer actually was pretty good until it started trashing any paper inserted and no directions to take it apart and see what was going on and they couldn't help - strange company................

---

