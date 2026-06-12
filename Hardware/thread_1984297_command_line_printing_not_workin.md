---
title: "command line printing not workin"
date: 2012-05-21
forum: Hardware
---

### Post by netopalis45 on 2012-05-21
Recently I have noticed that the lpr command to print using CUPS doesn't work in 10.10. I have used it in later versions and am quite confused as to why it isn't working now. I have set the default printer and can print by bringing up the document and using the print option in the File menu.

---

### Post by roelforg on 2012-05-21
> **netopalis45 said:**
> Recently I have noticed that the lpr command to print using CUPS doesn't work in 10.10. I have used it in later versions and am quite confused as to why it isn't working now. I have set the default printer and can print by bringing up the document and using the print option in the File menu.

According to the manpage ([http://manpages.ubuntu.com/manpages/maverick/en/man1/lpr.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/lpr.1.html)), you need to set the printer using lpoptions

---

### Post by netopalis45 on 2012-05-21
Already done that. Here is the output from lpstat -p -d

printer DCP-110C is idle.  enabled since Thu 03 May 2012 09:05:13 AM EDT
printer MFC490CW is idle.  enabled since Mon 21 May 2012 01:10:24 PM EDT
        Ready to print.
system default destination: MFC490CW

Trying to print to MFC490CW

---

### Post by roelforg on 2012-05-21
> **netopalis45 said:**
> Already done that. Here is the output from lpstat -p -d

printer DCP-110C is idle.  enabled since Thu 03 May 2012 09:05:13 AM EDT
printer MFC490CW is idle.  enabled since Mon 21 May 2012 01:10:24 PM EDT
        Ready to print.
system default destination: MFC490CW

Trying to print to MFC490CW

Then i don't know (never used printing below 11.04).

---

