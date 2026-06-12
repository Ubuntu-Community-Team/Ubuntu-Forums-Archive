---
title: "Xsane &quot;Invalid Argument&quot; on Supported Scanner"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by tarobs on 2007-01-06
I have a Genius ColorPage Vivid 4x Scanner. Whenever I run Xsane, it gives me the error: 

Failed to open device 'gt68xx:libusb:001:004':
Invalid argument.

I checked if my scanner is compatible with Xsane, and it is. What's causing the error then and how do I fix it?

Thanks in advance for those who would answer

---

### Post by bmt on 2007-01-07
Has it ever worked in Linux?  If not, you probably need to have a firmware file available to the sane backend.

If you go to the [sane search engine page]("http://www.sane-project.org/cgi-bin/driver.pl") and put in 'Genius', it will take you to more information about the parts of sane that support your scanner.  In the right-hand column of the table, it gives you a link to the manual page for more information.  Follow that link and see what it says there about the firmware file.

If you have a Windows installation that you have used the scanner with, the firmware file can be found there (do a file search for the filename).  Copy it to Ubuntu (more information on the location is in the sane manual page).

It's always worth trying a Google search on error messages.  In this case, if you search on "Failed to open device 'gt68xx" it gets a lot of links.

HTH.

---

