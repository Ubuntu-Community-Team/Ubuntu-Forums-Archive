---
title: "HP Printer issues"
date: 2011-09-15
forum: Hardware
---

### Post by Daibhi on 2011-09-15
I have installed 11.04 Ubuntu with no problems on a machine running an ASUS motherboard. I have a Officejet k60 printer running on USB which works fine in Win7 but when I try to use it in Ubuntu it freezes up. I usually have to power down printer then turn back on.

I was running the 3.11 cupps software for this driver, but upgraded to the new 3.17 from HP, is there something I'm missing here?

Thanks,

Daibhi

---

### Post by tgalati4 on 2011-09-15
Open a terminal and right after the printer freezes:

dmesg | tail -40

Post that and see what is going on.

Then:

cat /var/log/cups/error_log

---

### Post by Blasphemist on 2011-12-17
This may or may not be related to your issue but does seem to prevent a K60 from printing. I was getting an error message, There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

I had to go to the printer properties, make and model and select the HP Office Jet K60 instead of the generic text only that it showed from the printer recognition by Ubuntu 11.10. See screen shot.

---

