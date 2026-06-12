---
title: "HP Officejet 6210 with wireless printserver won't work"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by waldorf on 2005-12-30
Has anyone been able to get a HP Officejet 6210 to work with a wireless printserver?

Thanks in advance

---

### Post by daller on 2005-12-30
Have you got the printer working locally? (Is the printer working on ubuntu?)

Have you got other printers to work on the printserver? (Is the printserver working on ubuntu?)

Parallel or USB?

As far as I can see, the 6210 isn't supported (though, not listed as unsupported!)

I'd give the 6200 driver a try!

---

### Post by waldorf on 2005-12-30
Thanks. Your suggestion regarding the driver got me thinking and I figured out that the Deckjet 990c driver works because it is some sort of lowest common denominator driver.

So the set up is

ubuntu 5.10
linksys WPS54GU2
USB connection to the OfficeJet 6210
using Deskjet 990C driver

UNIX Printer (LPD) at xxx.xxx.xxx.xxx at L2

Is there some place I can put this information so that it can help others?

---

### Post by daller on 2005-12-30
[QUOTE=waldorf]Thanks. Your suggestion regarding the driver got me thinking and I figured out that the Deckjet 990c driver works because it is some sort of lowest common denominator driver.

So the set up is

ubuntu 5.10
linksys WPS54GU2
USB connection to the OfficeJet 6210
using Deskjet 990C driver

UNIX Printer (LPD) at xxx.xxx.xxx.xxx at L2

Is there some place I can put this information so that it can help others?[/QUOTE]

If the Deskjet 990C driver works for your printer (how did you sort that out?) you should send a "bug"-report to the hpoj/hpijs developers!

Join the mailing-list:

[http://hpoj.sourceforge.net/join.shtml](http://hpoj.sourceforge.net/join.shtml)

...And post a bug "solution"

Thank you for your help!

---

### Post by daller on 2005-12-30
I just posted the information on the mailing-list!

---

### Post by WADemosthenes on 2006-07-31
Hey, I have the exact same printer, I think (officejet 6210 all in one printer, scanner, copier, etc.).  How do you add a printer in xubuntu?  And can install it on one computer and share it with others in my network.  Thanks.

---

### Post by WADemosthenes on 2006-08-01
How do I add a printer in xubuntu?

---

### Post by daller on 2006-08-01
> **WADemosthenes said:**
> How do I add a printer in xubuntu?

Sorry, I don't use Xubuntu! (Not very often!)

I haven't installed a printer in Xubuntu...

Check out this wiki-page:

[https://wiki.ubuntu.com/XubuntuPrinterConfigSpec](https://wiki.ubuntu.com/XubuntuPrinterConfigSpec)

...though it doesn't tell you how! - It seems that you should install "gnome-cups-manager"!!!

Any help?

**AND BE PATIENT! - 15 hours is not a long time to wait for an answer!**

---

### Post by WADemosthenes on 2006-08-01
I'm just switching to ubuntu on all of my computers, much easier to get help :D  So how do you do it on ubuntu?

---

### Post by daller on 2006-08-01
Again, I'm using **K**ubuntu!

But again, it's a wiki-thing!

[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)

---

