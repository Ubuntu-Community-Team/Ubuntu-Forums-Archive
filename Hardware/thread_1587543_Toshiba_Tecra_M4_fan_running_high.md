---
title: "Toshiba Tecra M4 fan running high"
date: 2010-10-03
forum: Hardware
---

### Post by PTFunk on 2010-10-03
Hi all - I'm an Ubuntu newbie and just installed 10.1 release candidate on my Toshiba Tecra M4-S435 laptop.  After running for just a few minutes, the main cooling fan starts running on high speed, and often doesn't revert to a slower speed.  This doesn't appear to have a direct correlation with actual processor load, since it kicks in fairly arbitrarily.  Note that this Tecra model is known for having an active/noisy fan, but when I had it running under Windows XP it didn't have such sustained fan activity.

A Google search on the subject shows that in some cases this fan issue could be controlled on older Toshiba laptops with toshutils.  I've installed toshutils and also toshset, but can't find out how to run either, even from the command line.  For toshutils, the response is "command not found" and for toshset it comes back with "required kernel toshiba support not enabled".  

Any suggestions for getting either of these utilities to work?  I'd be happy to provide more info if needed.

Thanks!

-----------------
UPDATE 10/23/10: cleaned heat sink vanes and replaced fan with a used one off eBay.  After doing this and re-applying heat sink compound to CPU, the fan is running more quietly and less often.  Still would like a software solution, though!  From all the searching I've done it looks like toshset/toshutils needs kernel support that it hasn't gotten yet.

---

### Post by Jammerino on 2010-10-25
I purchased a used Toshiba Tecra M4-S435 Tablet PC and had problems from the beginning with it not booting (I was getting a PCI Express error message).  When it did boot to the desktop, the fan ran excessively and on very high.  I did eventually disassemble it and cleaned the cooling areas (heat sinks, fans, etc.).  After frequent and unpredictable boot-up, I eventually replaced the system board and now the fans run on normally.  As an aside, I believe the problem was with the NVidia video component of the Tablet PC.  I   So, my suspicions are that the reason for the fan running on high is hardware related, not the OS.

---

### Post by Jammerino on 2010-10-25
Just noticed you cleaned the heat sinks and cooling areas--and that it's running at a lower speed.  If your cooling areas were anything like mine, there was a half of an inch of dust completely obstructing the ducts and sinks... no wonder mine was running on high!

---

### Post by PTFunk on 2010-10-25
> **Jammerino said:**
> Just noticed you cleaned the heat sinks and cooling areas--and that it's running at a lower speed.  If your cooling areas were anything like mine, there was a half of an inch of dust completely obstructing the ducts and sinks... no wonder mine was running on high!
My cooling fins weren't too heinous, but benefitted from a clean.  I also think that the application of fresh heat sink compound to the CPU helped.  Now when the unit fully warms up, the fan seems to cycle between low (for a minute) and 'medium' (also for a minute), which isn't too noisy. 

From what I can tell the Toshiba extension to acpitool only allows running the fan in 'auto' mode or simply 'on'.  There's no incremental control, e.g. at a constant low speed.  So here's hoping the acpi gurus out there can develop something like this (unless I'm missing capabilities somewhere).

---

