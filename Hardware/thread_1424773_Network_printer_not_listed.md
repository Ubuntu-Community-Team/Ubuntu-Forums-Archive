---
title: "Network printer not listed"
date: 2010-03-08
forum: Hardware
---

### Post by raananb on 2010-03-08
I am trying to add to Ubuntu 9.10 a Canon MP550 multifunction printer connected to a networked Windows system.

The printer is detected through Samba, but when I try to select it from the list of printers this particular model is not included.

Debian drivers for the printer and the scanner are available at [http://support-au.canon.com.au/contents/AU/EN/0100236402.html](http://support-au.canon.com.au/contents/AU/EN/0100236402.html)

How can I finish the installation with MP550 as a remote printer?

---

### Post by tcchris on 2010-03-08
If you have the drivers installed , then you go to 
"localhost:631"
for the cups page , istall it from there 
I have a brother networked and this method works fine for me

---

### Post by raananb on 2010-03-08
Thanks.

There is no MP550 listed there (same list as the one brought up by the network dialog). The nearest is MP520. 

I guess the printer must be added to the list by someone knowledgable enough to do it to make it available to non-technical end users.

---

### Post by raananb on 2010-03-08
The solution to this issue when drivers for local installation are available:

Install the printer locally. This will create the ppd file for the printer, which can then be specified during the remote printer dialog.

For MP550, download drivers from [http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=All-in-One%20Printers&series=All-in-One%20Printers&model=PIXMA%20MP550&menu=Download](http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=All-in-One%20Printers&series=All-in-One%20Printers&model=PIXMA%20MP550&menu=Download) and install as advised at [http://ubuntuforums.org/showthread.php?t=1330314](http://ubuntuforums.org/showthread.php?t=1330314). The ppd file is /usr/share/cups/model/canonmp550.ppd

---

