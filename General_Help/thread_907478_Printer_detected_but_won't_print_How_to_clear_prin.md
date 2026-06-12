---
title: "Printer detected but won't print? How to clear print jobs?"
date: 2008-09-01
forum: General Help
---

### Post by Arrowx7 on 2008-09-01
Hello, 

I just plugged in my Epson Stylus C88+ USB printer (was used by a different computer) using a USB cable (using ubuntu 8.04 + all updates).  I tried running escputil -i -u -r /dev/usb/lp0 and it shows me all the ink levels, so I know the connection is fine.  I have it set up like this:  Gutenprint USB Printer #1 --> epson:/dev/usb/lp0 using the Epson Stylus C88 CUPS+Gutenprint v5.0.2 simplified driver.  When I try to print, it says "Processing" and then switches to "Held", and the printer does nothing.  Maybe there is some job that's bogging it down?  Is there any way to clear all 

Thanks!

---

### Post by plucky on 2008-09-01
> **Arrowx7 said:**
> Hello, 

I just plugged in my Epson Stylus C88+ USB printer (was used by a different computer) using a USB cable (using ubuntu 8.04 + all updates).  I tried running escputil -i -u -r /dev/usb/lp0 and it shows me all the ink levels, so I know the connection is fine.  I have it set up like this:  Gutenprint USB Printer #1 --> epson:/dev/usb/lp0 using the Epson Stylus C88 CUPS+Gutenprint v5.0.2 simplified driver.  When I try to print, it says "Processing" and then switches to "Held", and the printer does nothing.  Maybe there is some job that's bogging it down?  Is there any way to clear all 

Thanks!


Open Firefox or your Browser and in the address bar use ```
localhost:631/printers/
``` and see if you can cancel the jobs there.


Good Luck

---

### Post by wolfen69 on 2008-09-01
just double click the little printer icon on your panel. a list of jobs should show up.

---

