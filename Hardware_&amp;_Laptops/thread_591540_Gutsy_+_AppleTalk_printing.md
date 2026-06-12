---
title: "Gutsy + AppleTalk printing?"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by BLKessler on 2007-10-25
I'm trying to add an HP LaserJet 6MP to my Ubuntu 7.10 (Gutsy Gibbon) installation. I've got a network with seven hosts on it, and everything can print to this printer successfully except for Ubuntu.

The printer supports AppleTalk, and is connected to my network via an AsantePrint LocalTalk-to-Ethernet bridge. I have been following the instructions I found at [https://help.ubuntu.com/community/AppleTalk](https://help.ubuntu.com/community/AppleTalk), but I'm not feeling the love yet.

I've installed Netatalk (sudo apt-get install netatalk), and AppleTalk seems to be working fine: when I execute nbplkup, the output details all of the AppleTalk devices on my network, including the HP LaserJet 6MP I'm trying to configure. Here's the relevant portion:

[INDENT]HP LaserJet 6MP:LaserWriter[/INDENT]

The documentation next instructed me to edit the /etc/cups/printers.conf file, but one didn't exist on my fresh Gutsy installation. So I created one (sudo vi /etc/cups/printers.conf) and used the documentation above as a template, substituting my printer name in the three appropriate locations:

[INDENT]# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Mon 25 Apr 2005 02:02:39 PM PDT
<Printer HPLJ6MP>
Info HPLJ6MP
Location Local zone
DeviceURI pap://*/HP LaserJet 6MP/LaserWriter
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>[/INDENT]

Then, as directed, I downloaded a working PAP back end ([http://www.birdhouse.org/~mnep/pap](http://www.birdhouse.org/~mnep/pap)), gave it execute permissions (sudo chmod +x pap), and moved it into the proper CUPS location (sudo mv pap /usr/lib/cups/backend). I restarted CUPS (sudo /etc/init.d/cupsys restart), but was still unable to successfully add the printer.

So no love. Anybody have any tips on what to do next? The documentation at the Netatalk site ([http://netatalk.sourceforge.net/2.0/Netatalk-Manual](http://netatalk.sourceforge.net/2.0/Netatalk-Manual).**_pdf_**) isn't helpful enough either.

---

### Post by BLKessler on 2007-11-04
After looking some more, I have the sinking feeling that the problem is either with the PAP backend (less likely) or the printers.conf file (most likely). Does anybody know if something changed related to either of these two pieces between CUPS 1.1.23 and the 1.3 that comes with Ubuntu 7.10?

---

### Post by jamescoy on 2008-02-18
Must to my dismay, there has been no fix provided on this or any related posts. I'm having the same problem as a few of these guys i.e. installed netatalk, then ran nbplkup and no printer showed up. Now, my problem may be related to the fact that I'm running Kubuntu in emulation, but maybe that's the other guys' problem too?

Sure could use some help.

Thanks.

---

