---
title: "HP F340 printer help"
date: 2006-10-15
forum: Hardware &amp; Laptops
---

### Post by weasel fierce on 2006-10-15
Just bought an HP F340 printer, and it shows up in the supported printers, in the printer wizard setup in Ubuntu (Dapper)

However, when I try to print from openoffice or abiword, nothing happens whatsoever. Likewise, trying to print from a pdf doesnt give me anything. 

Any extra steps I need to take with this printer ?

---

### Post by FastZ on 2006-10-30
I just bought this all-in-one printer/scanner/copier today at Walmart.  Fantastic little piece of equipment.  Before I hooked it up, i booted into Windows and after setting up the printer and installing the drivers onto Windows, I connected the printer to my computer, after that was done, the printer added itself to my computer.  Test pages printed just fine, the scanner worked just fine.  Then, I booted back into Ubuntu Edgy and went to add a printer, the new printer shows up as HP DeskJet F300 and default driver is HPIJS for basic printing jobs.  It is recommended you use the HPLIP driver if you want to use the scanner feature.  

Weasel, check this site out and it might help you out.  If you get the HPLIP driver to install successfully, let me know, I'm having problems with dependencies with mine.

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_F300](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_F300)

This is the problem I run into when I try to run the self-running HPLIP driver for this printer/scanner.

```

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------

warning: There are 6 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
error: This installer cannot install this dependency for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

```

I've tried to install every gcc or C++ or C compiler type package I could find in Synaptic to see if I can get rid of this dependency issue but have had no luck so far.  If I figure it out, I'll post how I did it.

---

