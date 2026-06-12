---
title: "Canon Pixma ip4000 properties"
date: 2009-09-26
forum: Hardware
---

### Post by aarceng on 2009-09-26
My ip4000 works fine connected to Ubuntu except

[LIST]
[*]I can't find a way to clean the print heads
[*]It does not report ink levels
[/LIST]


How do I do these simple tasks?

---

### Post by chris.evers on 2009-10-12
I've installed inkblot to control the ink levels for my Canon iP4000. Out of the box it told me it didn't recognize any printers, but when running the program as root it did found the printer. If you've the same problem just run this command

sudo adduser *** lp

---

