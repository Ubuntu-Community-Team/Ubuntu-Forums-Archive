---
title: "Epson PX810FW Wireless multifunction printer"
date: 2010-09-04
forum: Hardware
---

### Post by scintilla13 on 2010-09-04
Ubuntu Lucid Recognize the printer automatically.

The driver is only able to print the first ubuntu test page. After the first real print trial the driver goes on error state and it doesn't print more.

On Printing state is reported longly: Work in progress, processing page 1 ...

Any idea?

---

### Post by scintilla13 on 2010-09-04
Now I'm able to see a new error on printer status

/usr/lib/cups/filter/pdftoraster failed

---

### Post by scintilla13 on 2010-10-16
Solved Today.

deleted printer.
Reinstalled using a nice wizard and selecting this kind of link

lpd://10.100.1.10:515/PASSTHRU

(this is not default one...)

---

