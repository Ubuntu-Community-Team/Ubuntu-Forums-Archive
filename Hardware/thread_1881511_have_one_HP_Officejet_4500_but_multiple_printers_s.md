---
title: "have one HP Officejet 4500 but multiple printers shown in system-config-printer 1.2.0"
date: 2011-11-15
forum: Hardware
---

### Post by Vpc on 2011-11-15
I upgraded from 8.04 to 10.04 in September. When I access System > Administration > Printing, I see multiple printers although I only have one connected i.e. I see:
  
* Officejet_4500_G510a-f (green check mark on left corner)
* Officejet_4500_G510a-f2
* Officejet_4500_G510a-fax
* Officejet_4500_G510a-fax2
* Officejet_4500_G510a-fax3
* PDF

Should I delete what seem to be duplicates e.g. the f2, fax2 and fax3?

---

### Post by Vpc on 2012-03-16
> **Vpc said:**
> I upgraded from 8.04 to 10.04 in September. When I access System > Administration > Printing, I see multiple printers although I only have one connected i.e. I see:
  
* Officejet_4500_G510a-f (green check mark on left corner)
* Officejet_4500_G510a-f2
* Officejet_4500_G510a-fax
* Officejet_4500_G510a-fax2
* Officejet_4500_G510a-fax3
* PDF

Should I delete what seem to be duplicates e.g. the f2, fax2 and fax3?

I was able to delete the duplicates without causing any problems. Also, by deleting all the printers and then re-installing the printer driver via Server -> New -> Printer, I was able to stop the printer from printing an extra blank page at the end of print jobs. When re-installing the driver, when you get to the "Select Device" step, make sure you select the printer and not the fax software. In my case, the printer was below the fax, which you would select if re-installing the driver for the fax function.

---

