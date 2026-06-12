---
title: "Brother mfc-9970cdw 11.10 problem."
date: 2012-01-22
forum: Hardware
---

### Post by CJH68 on 2012-01-22
I have just purchased a brother mfc-9970cdw colour laser prinet and  cannot print to it from my laptop with 11.10. I installed the driver in  software centre and can see the printer as MFC-9970CDW, Location --,  Model Generic PCL6/PCL XL Printer, IP Address localhost,Supply level,  Jobs 2 active (test print page and a print job from writer)

I open [http://localhost:631/printers/MFC-9970CDW-2](http://localhost:631/printers/MFC-9970CDW-2)   and see
[&#9660; ID &#9660;]("http://localhost:631/printers/MFC-9970CDW-2?QUERY=&WHICH_JOBS=&FIRST=%7BFIRST%7D&ORDER=dec")NameUserSizePagesStateControl     [MFC-9970CDW-2]("http://localhost:631/printers/MFC-9970CDW-2")-4  Unknown  Withheld  1k  Unknown   processing since
Sun 22 Jan 2012 05:07:22 PM EST 
*"Unable to locate printer "BRW0022587F12E6"."*          I can see th printer in the router as 3         **192.168.0.4**         **BRW0022587F12E6**         **00:22:58:7F:12:E6**
Can anyone advise as to what I should do? Many thanks in advance.
 I  cannot access the modify printer function in localhost as I get a  message A username and password are being requested by  [http://localhost:631](http://localhost:631). The site says: "CUPS"  and do not know the  password or username, have tried "root" with my PW as suggested in  another post, to no avail.

---

### Post by CJH68 on 2012-01-22
Managed to get it working after finding a suggestion to use system-config-printer instead of "printer control panel" from within 11.10.

---

### Post by mörgæs on 2012-01-22
Thanks for posting. Moved to the hardware forum.

Please mark a solved thread so using 'thread tools' - I have done it this time :-)

---

### Post by lkub on 2012-05-30
> **CJH68 said:**
> Managed to get it working after finding a suggestion to use system-config-printer instead of "printer control panel" from within 11.10.

I wonder if you've updated to Ubuntu 12 since then.  If so, does your Brother MFC-9970 work properly?
Here is why I'm asking: I'm thinking about buying MFC-9970 and using it under Ubuntu 12 but Brother's own web site ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00107](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00107)) indicates that Brother printers don't work properly under Ubuntu 12.
Any info would be greatly appreciated.
Many thanks,
lkub

---

