---
title: "Ubuntu 12.04 crashes my Brother HL-1470N printer"
date: 2013-10-20
forum: Hardware
---

### Post by Scott_Lindner on 2013-10-20
This is very odd.  I have had our Brother HL-1470N LASER network printer for a very long time and it has always worked fine from Windows.  I recently installed Ubuntu 12.04 Desktop to make the switch from Windows and most of the time it crashes or locks up the printer in a state that can only be recovered by a hard boot on the printer.  I cannot access the web administration console after attempting to print from Ubuntu.  I can print the Ubuntu test page without crashing the printer so I know it isn't entirely wrong.  Does anyone have any ideas of how to approach solving this?

---

### Post by Byb on 2013-12-15
Hi Scott
I get the same problem with the same printer. Did you get any help somewhere to have your 1470N work with Ubuntu? I am with 13.04

Thank you

In the end with test page I get a second page with:
```
ERROR:
limitcheck
OFFENDING COMMAND:
Type42BuildGlyph
STACK:
-mark-
-mark-
-mark-
```

---

### Post by Byb on 2013-12-15
I just reached to have my first print success : I changed the printer properties to
URI socket://10.xxx.xxx.101:9100 (unchanged)
Make/model : Brother HL-1470N - CUPS+Gutenprint v5.2.9
and selected "Use the new PPD file as is" in the last wizard config pop-up window (non default option)
 
BR-Script2 and foomatic/postscript didn't work

---

### Post by Scott_Lindner on 2013-12-15
I tried making changes like that without any luck.  I don't recall if I tried exactly what you mentioned above, but I ended up giving up on both Ubuntu for the desktop OS and dumping the printer.  There were a lot of reasons why I went this direction.  This issue was a minor contributor.  I'm glad you got it working.  Thanks for sharing your results!  That was driving me batty.

---

