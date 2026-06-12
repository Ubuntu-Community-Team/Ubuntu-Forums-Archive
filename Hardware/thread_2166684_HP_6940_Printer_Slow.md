---
title: "HP 6940 Printer Slow"
date: 2013-08-10
forum: Hardware
---

### Post by tbzep on 2013-08-10
Ever since upgrading to 13.04 via clean install, my printer has become very slow, taking minutes per page, often sitting idle for minutes then printing one line before sitting idle again.  This has never been an issue dating back to 8.x.   Watching my resources on conky during printing, I never see my cpu or memory taxed.  I have removed and reinstalled hplip and the printer.  It occurs with all file types.  The printer is an HP 6940 connected via USB.

---

### Post by bsamim on 2013-08-11
I had so many issues with the hplip drivers, I also am connected via usb without issues now. I am currently using the following with my hp printer with no issues.  Just delete the existing printer and configure it through the cups web site and try using the following driver.

HP LaserJet 1200 - CUPS+Gutenprint v5.2.9

---

### Post by tbzep on 2013-08-16
> **bsamim said:**
> I had so many issues with the hplip drivers, I also am connected via usb without issues now. I am currently using the following with my hp printer with no issues.  Just delete the existing printer and configure it through the cups web site and try using the following driver.

HP LaserJet 1200 - CUPS+Gutenprint v5.2.9

I don't have a laser printer.  The 6940 is an inkjet.

---

