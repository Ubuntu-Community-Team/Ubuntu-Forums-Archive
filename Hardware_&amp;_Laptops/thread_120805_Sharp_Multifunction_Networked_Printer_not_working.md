---
title: "Sharp Multifunction Networked Printer not working"
date: 2006-01-23
forum: Hardware &amp; Laptops
---

### Post by SuperDiscoMachine V.5.7-3 on 2006-01-23
We are trying to set up Ubuntu to work in a small not-for-profit office setting, but we are having difficulty getting our Sharp Multifunction Networked Printer (the AR-M450) to work.

Sharp offers driver downloads that have been tested on Red Hat, and we installed them, and then set the printer up as a CUPS printer, using ipp://192.168.2.200 as the URI.

When we try to print a test page, the printer doesn't do anything.  We've tried configuring it as 
[LIST]
[*]ipp://192...200
[*]ipp://192...200/ipp/
[*]ipp://192...200/ipp/port1
[/LIST]

Any suggestions?

(Running Ubuntu Breezy Badger single-boot on a HP Pavillion desktop)

Thanks in advance for any  help you can provide!!

---

### Post by mips on 2006-01-23
[http://www.linuxprinting.org/sharp-faq.html#q_4_1](http://www.linuxprinting.org/sharp-faq.html#q_4_1)
> 4.1 Does this printer work with free software? 
Yes. This printer understands PostScript and PCL. For PCL, try the HP LJ8000 or similar driver.

You have three options. First try the HP LaserJet 8000 series drivers and see how it goes. Secondly you can simply configure it as a Postscript printer and not worry about a driver. Third you can try and configure it using a Generic PCL driver.

Some drivers here, [http://www.indyofficesolutions.com/downloads.php](http://www.indyofficesolutions.com/downloads.php)
Dunno how they work as it basically looks like a text config file, sure it can be adapted or made to work...

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-01-31
Thanks, Mips, I had already seen those sites in my travels, and still not been able to get anything to work, but I'm posting what did work, so anyone else won't have to go through everything we tried.

1. We downloaded the driver from [http://www.sharp.ca/downloads/](http://www.sharp.ca/downloads/) (Choose "Copier" and then the type of MFP)
2. The driver is in exe format for some strange reason, so we needed to uncompress it, and pull out the needed PPD to install
3. We used the printer setup utility to install the driver, and configured the printer as a LPD printer (not CUPS) with the IP address as the Host, and left the Queue empty

Hope this info helps someone else!

---

### Post by mips on 2006-01-31
have you tried the default HP & PS drivers that come with Ubuntu ?

Configure it as a normal TCP Network printer. I use kde so things look abit different.

What are the IP settings for the PC & Printer (IP, Netmask, Default gateway etc) ???

---

