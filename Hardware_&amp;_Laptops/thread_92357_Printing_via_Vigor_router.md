---
title: "Printing via Vigor router"
date: 2005-11-19
forum: Hardware &amp; Laptops
---

### Post by Cuppa-Chino on 2005-11-19
Am trying to print on my Epson Stylus C60 that is attached via USB to my Vigor Router 2600G. It works fine under Windofs when I follow the instructions from the Vigor support page: [Vigor Support Page for LPR printing]("http://www.draytek.co.uk/support/kb_vigor_lpr_setup.html"), at the bottom of the page linux is briefly mentioned:
> **Using the Vigor's printer port from Linux**
Linux is not officially supported for printing facilities, however it may be possible to access the printer port LPR facility by configuring CUPS using the parameter: lpd://192.168.1.1/p1. 

I have tried entering the code mentioned, **lpd://192.168.1.1/p1**, into the Gnome Printer Setup (connection set as CUPS) but does not work, when I reopen the printer the code has an additional **ipp://** infront of it. If I delete the **lpd://** :arrow: so that CUPS connection is **ipp://192.168.1.1/p1** my printer still does not respond.

Any ideas? I have scanned the forums and found these related threads but they do not really help me:
[LIST]
[*][samsung laser printer across the network? ]("http://www.ubuntuforums.org/showthread.php?t=59282&highlight=vigor+router+printer")
[*][Dual Boot PC]("http://www.ubuntuforums.org/showthread.php?t=92339&highlight=vigor+router+printer")
[/LIST]

---

### Post by Cuppa-Chino on 2005-11-19
:oops: found the answer myself...

had to choose **UNIX Printer (LPD)** not CUPS as in the Vigor instructions! Has printed now! :p

So Mini instructions are:
[LIST]
[*]connect everything as under Windows
[*]enter the pure ip-address into the **Host:** box - no *lpd://* needed in front
[*]enter the **Queue:**, I used p1 as in the Windows tutorial on the Draytek homepage
[/LIST]

---

