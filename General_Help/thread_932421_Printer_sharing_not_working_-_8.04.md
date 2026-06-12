---
title: "Printer sharing not working - 8.04"
date: 2008-09-28
forum: General Help
---

### Post by lowracer on 2008-09-28
Printer sharing isn't working.

I have a Dell Inspiron 1525 running 8.04. Kernel 2.6.24-19 generic.  Gnome 2.22.3. This was one of those dells that came preloaded with Linux.

The printer is a Samsung ML2151N connected to an intel Quadcore PC also running 8.04. The Printer configuration for this printer has it Enabled/Accepting Jobs/Shared, and Access control is wide open, Allow printing for everyone.

When I try to print to the shared printer from the laptop, the job goes into the print queue and stays there forever without printing.  When I go to Administration --> Printing on the laptop, if I select the shared printer (Samsung ML2151N), the Printer configuration control panel will hang.  It has to be force-quit.  

I used the troubleshoot feature of the Printer configuration panel on the laptop and it told me that there are status messages associated with this queue. Printer's state message: recoverable: Unable to connect to printer; will retry in 30 seconds...
Printer's state reasons: connecting-to-device.

The printer that is being shared works for local printing.  I just can't print to it from the laptop.  The laptop and desktop are both behind a common router, and get their IP addresses via DHCP.

What could be going on here?  I'm at wits end.  Everytime my wife wants to print something from the laptop downstairs, she emails it to me to print on my machine upstairs.  That's getting old.

Thanks,
-Mark
aka lowracer

---

### Post by taladan on 2008-09-28
I had a similar issue with an HP Deskjet 6940, I finally resolved it by changing how I had it added as a share (I'm using Kubuntu so the steps aren't the same), All my computers that stay up all the time on my network are statically assigned, so I set it up to print via tcp to ipp://<IP ADDRESS>:631/printers/Deskjet_6940_series

I don't know about ubuntu, but I know in kubuntu you force the printer wizard to scan a tcp subnet to detect printers looking for a CUPS server/share.  Someone else may be able to step you through the menus to do this on your client, but that's probably the issue you're facing.

Tal

---

