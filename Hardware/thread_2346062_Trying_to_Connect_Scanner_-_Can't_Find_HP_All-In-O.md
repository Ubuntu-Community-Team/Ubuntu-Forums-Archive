---
title: "Trying to Connect Scanner - Can't Find HP All-In-One From IP Address w/ Command Line"
date: 2016-12-10
forum: Hardware
---

### Post by ktc2 on 2016-12-10
Had/having trouble getting our two Ubuntu machines to recognize the scanner on my new HP All-In-One (OfficeJet Pro 8710). Printer worked fine with both machines, and is easy to find/manipulate using printer utility in system settings. Scanner, however, couldn't be detected by either computer. 

For my machine, running Ubuntu 16.10, scanner connectivity was a fairly easy fix: found uri with "hp-makeuri <IP Address>" in terminal; manually changed DeviceURI to CUPS URI in CUPS using "sudo nano /etc/cups/printers.conf;" restarted CUPS with "sudo /etc/init.d/cups restart." It worked like a dream, and scanner is now findable and usable in both XSane and SimpleScan. 

On my wife's machine, running Ubuntu 16.04, when I tried "hp-makeuri <IP Address>" a "device not found" error message returned. When I manually edited Device URI in CUPS on her comp, to the same CUPS URI that worked on my comp, using "sudo nano/etc/cups/printers.conf," nothing happened. 

We're on the same home wifi network; printing works fine from her comp, and printer is easily findable with printer utility; I also manually went back and checked that my modification to CUPS had saved. 

Can anyone help me figure out why a working, usable, network connected printer wouldn't be findable with command line using IP address; why a manual modification to CUPS wouldn't work anyway; and how to fix these things? 

Keep in mind, I'm kind of a newbie. I don't know much about programming. In other words, I'm able to follow clear instructions for command line entries, but I don't really understand anything about why they work (although I'd like to!) 

Clear, simple instructions will be greatly appreciated, and don't worry about talking down to me! I'm at a child level of understanding coding (except that a lot of children these days probably know more about it than I do!) 

THANKS FOR ANY HELP!

---

