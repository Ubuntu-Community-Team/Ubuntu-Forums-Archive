---
title: "Print problem in Maple 11"
date: 2008-09-28
forum: General Help
---

### Post by dclement on 2008-09-28
Hello,

I have a problem in Hardy 8.04.1 with the Maple 11 computing (not free) software: cannot print!

In Maple 11, the print dialog (which is not standard) shows for all printers: "refuse tasks". If I try however, nothing happens. Even if the program is run as root.

But if Maple 11 is run from a terminal, I get the following:
--
java.awt.print.PrinterException: Printer is not accepting job.
at sun.print.RasterPrinterJob.print(Unknown Source)
at sun.print.RasterPrinterJob.print(Unknown Source)
at com.maplesoft.worksheet.controller.file.WmiWorksheetFilePrint.doCommand(Unknown Source)
at com.maplesoft.mathdoc.controller.WmiCommandProxy.doCommand(Unknown Source)
at com.maplesoft.mathdoc.controller.WmiTaskMonitor.performCommand(Unknown Source)
at com.maplesoft.mathdoc.controller.WmiTaskMonitor$WmiBackgroundTaskRunner.run(Unknown Source)
--
My Maple 11 install is quite basic except that I put it under /opt instead of the default /root.

What can explain this? 

TIA for any help - regards, Daniel

---

