---
title: "XSane Scan Failure"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by nstannik on 2007-08-29
Hi,

     I'm having a scanning problem with an HP F-380 PSC and XSane. The problem is this: when I open XSane (version 0.991) it successfully finds my device, but when I click "Scan", it freezes up. I can still force quit and use other apps, but nothing in the program itself.  Eventually (less than a minute) I get an error box that says "Error during device I/O". When I click OK in the error box, it goes right back to the XSane windows, but never scans. When I run it through the terminal, there are no error messages at all.

     On the actual scanner the power on/off light blinks steadily after I try to scan the first time. If I try to scan again, XSane scans for devices but then disappears, although the program is still running (I can see it hasn't shut down through terminal). If I turn the scanner off and back on, it seems fine but I get the same problem.

     I'm running Feisty 7.04 on an HP a1410y with a Pentium 4 (3.06 GHz) CPU. The printer copies and prints fine. It is attached via USB and uses the "hpijs" driver. I have the HPLIP toolbox installed, which works fine and doesn't show any errors. I have no other printers connected, except two over a home network.

     So far I've tried reinstalling XSane (to no avail) as well as trying out two other USB ports, both of which I know to work. I also tried to scan in Windows XP (same machine, dual-boot) but the scanner hangs up there, too. I also had this problem in Dapper (before I upgraded to Feisty). This would lead me to believe that the problem is with the actual scanner, not the software, but I'm hoping someone out there can offer some advice.....

Please let me know if you need more information, attachments, etc.

Thanks in advance,

Nils

UPDATE: The scanner doesn't actually copy I just discovered. Maybe the problem is the scan-bed itself.....?

---

### Post by geraldm on 2007-08-31
The blinking light after the failed scan may be a coded message hint detailed in the user manual.

Just guessing about the I/O error:
I would try unloading all driver modules related to printing or print daemons.
Then try xsane.
This would isolate the problem to the scanner portion by removing any possibility of
interference from the printing drivers. 

Gerald

---

