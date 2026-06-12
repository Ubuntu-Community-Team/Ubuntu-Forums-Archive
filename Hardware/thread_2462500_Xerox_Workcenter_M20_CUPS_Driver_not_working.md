---
title: "Xerox Workcenter M20 CUPS Driver not working"
date: 2021-05-22
forum: Hardware
---

### Post by vladb57 on 2021-05-22
Good day,

I have recently installed ubuntu 21.04 and i was trying to make my Xerox Workcenter M20 work. While Ubuntu can correctly identify the printer, even manually selecting a driver from the library or installing the .deb file downloaded from openprinting does not prevent my printer from printing "%%!PS-Adobe-3.0 %%Incocaton: gs - q -dNOPAUSE" gibberish instead of any file i try to print (including the test print).

Is it at all possible to make this old printer work with ubuntu?

Thank you in advance.

---

### Post by him610 on 2021-05-23
From your description, sounds like the wrong driver is loaded.
Your printer specs say it may be connected by Direct Connect to PC (USB); Parallel Port, IEEE 1284. How is yours connected? 
You say you downloaded from [https://www.openprinting.org/printer/Xerox/Xerox-WorkCentre_M20]("https://www.openprinting.org/printer/Xerox/Xerox-WorkCentre_M20") , there are several files listed - which one did you select to download?

Can you tell us how you configured your printer with the cups configuration tool (system-config-printer) - each step in the sequence?

I don't know if I can help or not, but I'll try.

---

