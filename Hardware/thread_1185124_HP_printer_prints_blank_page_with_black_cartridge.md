---
title: "HP printer prints blank page with black cartridge"
date: 2009-06-11
forum: Hardware
---

### Post by Camilia on 2009-06-11
I have a deskjet printer 3930.

Document appears to be printing but get blank page.

In HPLIP tool box printed test page and it printed normal. At [http://localhost:631/printers/Deskjet-3900](http://localhost:631/printers/Deskjet-3900) test page printed blank. 

In HPLIP changed the printout cartridge to black. At cups found the cartridge was set to color cartridge, which I no longer have. Changed it to back cartridge [here]("http://localhost:631/admin/?op=set-printer-options&printer_name=Deskjet-3900") Cup settings not remaining as I set them. Reset the settings.

Alas it is working!! Worked for 1 day.

The settings in cups is always reset to colored cartridge. Thus decided to keep colored cartridge, which is very low, and black cartridge in the printer. Now it is printing in black. I also get the notification that the ink level is low. 

Printed black 1 time. Now printing purple.

I a got the printer to work. I am ecstatic!

I read the instruction for testing printer in ubuntupocketguide-v1-1.pdf. Follow instructions to print a test. System > Administration > Printing, then double-clicked the printer&#8217;s icon and clicked the PRINT TEST PAGE button. Result was blank page. In printer settings changed print out mode to black cartridge. Now it prints. It seems printout mode has to be set at 3 locations, printing, HPLIP, and CUPS.

Went to [CUPS]("http://localhost:631/printers/Deskjet-3900") to check the print out setting and now it stay in black cartridge print out mode.

---

