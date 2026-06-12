---
title: "Scan fails, can not connect to the scanner"
date: 2017-01-12
forum: Hardware
---

### Post by Hendrik_Van_Marcke on 2017-01-12
Hi there,

There is an all-in-one Brother printer installed on my computer.
However it seems i have a problem with scanning a document.

Here's the problem:

When i open a terminal and do:

```
gksudo simple-scan
```

The scanner works great

But when i try to scan as normal user i got the message: "Scan fails, can not connect to the scanner".

What could be the solution to that?

---

### Post by IPEX-731BA5DD06 on 2017-01-18
I have a MFC-L2073DW, Brother printer, I had the same problem.

Your solution worked for me.

I think the Brother scanner drivers installed from brother are out of date, or not working at all.

[www.brother.com](www.brother.com)

Go to Device support, it'll take you to Linux drivers, download what you need.

Use the RPM as the 1st needs a password to unzip, WHAT PASSWORD????

Any other suggestions ???

---

### Post by pdc on 2017-01-19
Hi there Hendrik;

on this page, [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) that is called "Scanner Use for Normal User" 

you can see you need to download this tiny debian-format file; install it; (your download system should offer to "open" it as it downloads it ......... "open" in this context should mean "install" ...................)

........ you will be downloading [COLOR="#008000"]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR] ............

and you should be able to access the scanner as a normal user  ...................

....... it adds a line to the file [COLOR="#008000"]40-libsane.rules[/COLOR] that lives inside [COLOR="#008000"]/lib/udev/rules.d[/COLOR] .............

---

