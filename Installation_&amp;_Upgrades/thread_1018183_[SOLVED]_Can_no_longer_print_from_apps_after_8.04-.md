---
title: "[SOLVED] Can no longer print from apps after 8.04-&amp;gt;8.10 upgrade"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by Defrector on 2008-12-21
Cannot print from apps after 8.04(32bit)->8.10(32bit) upgrade. Please help if willing:

Brother HL-2700CN Color Laser, ethernet, by IP. Uses (and reinstalled) .PPD file. Has worked before dist-upgrade. I believe it is using CUPS and/or BR-script.

When attempting to print from kNotes, OpenOffice.org, or Okular, network printer's LCD display shows "PROCESSING" as if it was about to print, then aborts and goes back to "READY" as if nothing happened.

Print jobs window reflects this. All appears fine and then the job is quietly aborted.

Nothing shows up in /var/log/cups when this is attempted. No odd messages in /var/log so far.

In the printer configuration app, I CAN print a ubuntu test page like usual. This is the only situation where I can get the print to go through so far.

telnet into printer does not appear to show any logs hinting at the problem.

:confused:

---

### Post by Defrector on 2008-12-24
SOLVED!:KS

Did apt-get update, big CUPS update; prints fine so far. Versions installed are below if you would like to check yours:

cups
cups-bsd
cups-client 
cups-common 
cupsys 
cupsys-bsd 
cupsys-client 
cupsys-common 
libcups2 
libcupsimage2 
libcupsys2 

...appear to be all updated to 1.3.9.2-ubuntu6.

---

