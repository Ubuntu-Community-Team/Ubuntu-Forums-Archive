---
title: "Printer suddenly stopped working"
date: 2010-04-16
forum: Hardware
---

### Post by ubiqx on 2010-04-16
Hello,

My printer suddenly stopped working. It was working fine for quite some time, but suddenly print jobs make it to the queue (as seen from the CUPS web interface) and just sit there.

I've done some basic troubleshooting and have come across the following:

[LIST]
[*]I'm running Kubuntu 8.04 Hardy Heron.
[*]The printer is turned on and plugged in.
[*]Updating the system and restarting the machine has not solved anything.  (No updates were performed prior to the sudden loss of printing capabilities.)
[*]The printer works when the machine is rebooted under Windows, so the printer and USB ports seem to be working.
[*]CUPS detects the printer just fine. I can turn-off/unplug the printer and then turn it back on/plug it back in and ubuntu succeeds in automatically detecting it and configuring it. I can even delete the printer using the web interface and it still shows up properly configured when I plug it back in.
[*]I'm seeing temp files for the print jobs and the ghostscript files. The printer doesn't show any signs of activity regardless.
[*]Removing (purging) and reinstalling the cupsys package by force didn't solve anything. Doesn't seem to have broken anything further, at least.
[*]Printing to the PDF converter, or to a remote printer, works.
[*]About the only useful bit of info I've got is when I try to click "Print Self-test Page" from the web interface on the printer, the status changes to: 
**[SIZE=1]"/usr/lib/cups/filter/pstoraster failed"[/SIZE]**
[/LIST]
I've attached the output from printingbuginfo and a zip of what I believe to be the relevant portion of the /var/log/cups/error_log with LogLevel set to 'debug', in hopes that it may be of some help.

---

